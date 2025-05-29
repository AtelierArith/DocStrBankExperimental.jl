```
load_camb_Cℓs(;path_prefix, custom_tensor_params=nothing, 
    unlensed_scalar_postfix, unlensed_tensor_postfix, lensed_scalar_postfix, lenspotential_postfix)
```

Load some Cℓs from CAMB files. 

`path_prefix` specifies the prefix for the files, which are then expected to have the normal CAMB postfixes: `scalCls.dat`, `tensCls.dat`, `lensedCls.dat`, `lenspotentialCls.dat`, unless otherwise specified via the other keyword arguments. `custom_tensor_params` can be used to call CAMB directly for the `unlensed_tensors`, rather than reading them from a file (since alot of times this file doesn't get saved). The value should be a Dict/NamedTuple which will be passed to a call to `camb`, e.g. `custom_tensor_params=(r=0,)` for zero tensors. 
