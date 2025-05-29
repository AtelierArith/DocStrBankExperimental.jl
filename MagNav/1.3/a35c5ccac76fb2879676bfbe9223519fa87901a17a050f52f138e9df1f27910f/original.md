```
comp_test(comp_params::CompParams, xyz::XYZ, ind,
          mapS::Union{MapS,MapSd,MapS3D} = mapS_null;
          temp_params::TempParams        = TempParams(),
          silent::Bool                   = false)
```

Evaluate performance of an aeromagnetic compensation model.

**Arguments:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
  * `xyz`:         `XYZ` flight data struct
  * `ind`:         selected data indices
  * `mapS`:        (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct, only used for `y_type = :b, :c`
  * `temp_params`: (optional) `TempParams` temporary temporal parameters struct
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `y`:        length-`N` target vector
  * `y_hat`:    length-`N` prediction vector
  * `err`:      length-`N` compensation error
  * `features`: length-`Nf` feature vector (including components of TL `A`, etc.)
