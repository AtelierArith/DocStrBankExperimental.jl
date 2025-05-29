```
save_comp_params(comp_params::CompParams,
                 comp_params_bson::String = "comp_params.bson")
```

Save aeromagnetic compensation parameters to BSON file.

**Arguments:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
  * `comp_params_bson`: (optional) path/name of aeromagnetic compensation parameters BSON file to save (`.bson` extension optional)

**Returns:**

  * `nothing`: `comp_params_bson` is created
