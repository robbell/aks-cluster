# AKS Cluster

![CI](https://github.com/robbell/aks-cluster/workflows/CI/badge.svg)

Creation of an AKS cluster using Ansible.

## Prerequisites

1) Create a service principal using the below, keeping track of the generated JSON:

    `az ad sp create-for-rbac --name ServicePrincipalName --sdk-auth`

1) Update the project secrets to the following using the service principal JSON output above:

    * `AZ_CREDENTIALS` set to use the entire JSON block. This is used by the `azure\login` GitHub action to provision the cluster
    * `CLIENT_ID` set to the `clientId` from the JSON block. This is used to allow the SP to connect to the cluster
    * `CLIENT_SECRET` set to the `clientSecret` from the JSON block. This is used to allow the SP to connect to the cluster
    * `SSH_KEY` set to single line SSH RSA from the JSON block. This is used as the public key to connect to the cluster. This can be found in C:\Users\\[username]\\.ssh\id_rsa.pub
