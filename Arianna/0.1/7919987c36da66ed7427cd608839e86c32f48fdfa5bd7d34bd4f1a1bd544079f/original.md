```
StoreParameters(chains; dependencies=missing, path=missing, ids=missing, store_first=true, store_last=false, extras...)
```

Create a new StoreParameters instance.

# Arguments

  * `chains`: Vector of chains to store the parameters of
  * `dependencies`: Dependencies of the parameter store
  * `path`: Path to the parameter files
  * `ids`: IDs of the parameters to store
  * `store_first`: Flag to store the parameters at the first step
  * `store_last`: Flag to store the parameters at the last step
  * `extras`: Additional keyword arguments

# Returns

  * `algorithm`: StoreParameters instance
