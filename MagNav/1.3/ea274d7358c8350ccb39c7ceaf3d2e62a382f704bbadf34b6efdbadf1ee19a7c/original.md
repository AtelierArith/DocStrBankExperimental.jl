```
get_comp_params(comp_params_bson::String, silent::Bool = false)
```

Get aeromagnetic compensation parameters from saved BSON file.

**Arguments:**

  * `comp_params_bson`: path/name of aeromagnetic compensation parameters BSON file (`.bson` extension optional)
  * `silent`:           (optional) if true, no print outs

**Returns:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
