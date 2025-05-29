```
comp_train_test(comp_params::CompParams,
                xyz_train::XYZ, xyz_test::XYZ, ind_train, ind_test,
                mapS_train::Union{MapS,MapSd,MapS3D} = mapS_null,
                mapS_test::Union{MapS,MapSd,MapS3D}  = mapS_null;
                temp_params::TempParams = TempParams(),
                silent::Bool            = false)
```

Train & evaluate performance of an aeromagnetic compensation model.

**Arguments:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct, either:

      * `NNCompParams`:  neural network-based aeromagnetic compensation parameters struct
      * `LinCompParams`: linear aeromagnetic compensation parameters struct
  * `xyz_train`:   `XYZ` flight data struct for training
  * `xyz_test`:    `XYZ` flight data struct for testing
  * `ind_train`:   selected data indices for training
  * `ind_test`:    selected data indices for testing
  * `mapS_train`:  (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct for training, only used for `y_type = :b, :c`
  * `mapS_test`:   (optional) `MapS`, `MapSd`, or `MapS3D` scalar magnetic anomaly map struct for testing,  only used for `y_type = :b, :c`
  * `temp_params`: (optional) `TempParams` temporary temporal parameters struct
  * `silent`:      (optional) if true, no print outs

**Returns:**

  * `comp_params`: `CompParams` aeromagnetic compensation parameters struct
  * `y_train`:     length-`N_train` training target vector
  * `y_train_hat`: length-`N_train` training prediction vector
  * `err_train`:   length-`N_train` training compensation error
  * `y_test`:      length-`N_test` testing target vector
  * `y_test_hat`:  length-`N_test` testing prediction vector
  * `err_test`:    length-`N_test` testing compensation error
  * `features`:    length-`Nf` feature vector (including components of TL `A`, etc.)
