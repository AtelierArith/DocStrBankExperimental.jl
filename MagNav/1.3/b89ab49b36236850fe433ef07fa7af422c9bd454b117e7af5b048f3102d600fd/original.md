```
comp_train(comp_params::CompParams, xyz_vec::Vector, ind_vec::Vector,
           mapS::Union{MapS,MapSd,MapS3D} = mapS_null;
           temp_params::TempParams        = TempParams(),
           xyz_test::XYZ                  = xyz_vec[1],
           ind_test                       = BitVector(),
           silent::Bool                   = false)
```

Train an aeromagnetic compensation model.

**Arguments:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
  * `xyz_vec`:     vector of `XYZ` flight data structs
  * `ind_vec`:     vector of selected data indices
  * `mapS`:        (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct, only used for `y_type = :b, :c`
  * `temp_params`: (optional) `TempParams` temporary temporal parameters struct
  * `xyz_test`:    (optional) `XYZ` held-out test data struct
  * `ind_test`:    (optional) indices for test data struct
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct
  * `y`:           length-`N` target vector
  * `y_hat`:       length-`N` prediction vector
  * `err`:         length-`N` compensation error
  * `features`:    length-`Nf` feature vector (including components of TL `A`, etc.)
