```
showconst(
    query::Symbol = :constants
)
```

## Description:

list available constants in the package

## parameters:

  * `query`     – type:`Symbol`, the type of constants you want to know about

## options:

  * `:constants`      – list all physical constants
  * `:subatomic`      – list all possible subatomic particles
  * `:(atomic symbol)`– list all isotopes of that atomic species, e.g. :Fe
