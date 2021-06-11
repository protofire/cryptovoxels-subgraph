# Cryptovoxels Subgraph

This subgraph is deployed at: https://thegraph.com/explorer/subgraph/protofire/cryptovoxels

Most of this subgraph was forked from https://github.com/ZoltarSeven/cryptovoxels-subgraph
This subgraph tracks parcels, names, wearables and accounts in the Cryptovoxels virtual world. 

## Installation
This repo is using yarn. After cloning, run :
```
$ yarn install && yarn codegen
```
## Key Entity Overviews

#### Parcel
Contains data concerning parcels such as buildHeight, length, width, area and has relationship with the Account entity.
**Example query**
```
{
  parcels(first: 5) {
    id
    tokenID
    location
    buildHeight
    area
    length
    width
    volumeInVoxels
    owner {
      id
    }
    createdAt
    tokenURI
  }
}

```
#### Name
Contains data regarding a name and its relationship with the Account entity.
**Example query**
```
{
  names(first: 5) {
    id
    tokenID
    name
    owner {
      id
    }
    createdAt
  }
}
```

#### Wearables
Contains data regarding a wearable edition, such as its rarity and derives an array of the owners via the AccounWearable entity.
The uri field contains the address for downloading de .vox file.
**Example query**
```
{
  wearables(first: 5) {
    id
    owners {
      id
      account {
        id
      }
    }
    initialQuantity
    currentQuantity
    author
    rarity
    createdAt
    category {
      id
      tokenID
    }
    uri {
      id
      uri
    }
  }
}
```
#### Account
Contains information concerning each account and its parcels, names and wearables derived from each respective entity.
**Example query**
```
{
  accounts(first: 5){
    id
    address
    parcel {
      id
    }
    name {
      id
    }
    wearable {
      id
    }
  }
}
```
