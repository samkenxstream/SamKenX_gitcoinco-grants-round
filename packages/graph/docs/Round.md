**Fetch all rounds created**

```graphql
{
  rounds {
    id
  }
}
```

**Fetch accounts (with their roles) & program of all rounds**

```graphql
{
  rounds {
    id
    program
    accounts {
      address
      role {
        role
      }
    }
  }
}
```

**Fetch all rounds created by a program**

```graphql
{
  rounds(where: {
    program: "0x1564f459600505734cffe7a075691db96e517ae7"
  }) {
    id
  }
}
```


**Fetch all rounds managed by a specific account with thier role**

```graphql
{
    roundAccounts(where:{
      address:"0x5cdb35fadb8262a3f88863254c870c2e6a848cca"
    }) {
      address
    	role {
        role
      }
      round {
        id
      }
    }
}
```

**Fetch all rounds managed by a specific account with a specific role**

```graphql
{
  roundRoles(
    where :{
      role:"0xec61da14b5abbac5c5fda6f1d57642a264ebd5d0674f35852829746dfb8174a5"
    }
  ) {
    accounts(where:{
      address:"0x5cdb35fadb8262a3f88863254c870c2e6a848cca"
    }) {
      address
      round{
        id
      }
    }
  }
}
```

**Fetch accounts having a specific role on a specific round**

```graphql

{
  rounds(where :{
    id:"0x804629a3aa09502a9893fd4ca58007087a34efe9"
  }) {
  	roles(where:{
      role:"0xec61da14b5abbac5c5fda6f1d57642a264ebd5d0674f35852829746dfb8174a5"
    }) {
      accounts {
        address
      }
    }
  }
}
```


**Fetch all accounts & their roles in a specific round**
```graphql
{
  rounds(where :{
    id:"0x804629a3aa09502a9893fd4ca58007087a34efe9"
  }) {
    accounts {
      address
      role {
        role
      }
    }
  }
}
```

**Fetch all rounds by a project id and know it's status**

You can do this by two means :
##### Filtering against the round

```graphql
{
  rounds(where:{
    id: "0x7581e65b04da761ef3311997ec04bf3046013c96"
  }) {
    id
    projects {
      id
      status
      metaPtr {
        protocol
        pointer
      }
    }
  }
}
```

##### Filtering against the roundProject


```graphql
{
  roundProjects(where: {
    round:"0x7581e65b04da761ef3311997ec04bf3046013c96"
  }) {
    id
    status
    metaPtr{
      protocol
      pointer
    }
    round {
      id
    }
  }
}
```