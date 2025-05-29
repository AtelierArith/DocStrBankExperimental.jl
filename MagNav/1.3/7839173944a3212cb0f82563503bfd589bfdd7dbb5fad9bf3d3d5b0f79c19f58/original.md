```
TL_vec2mat(TL_coef::Vector, terms; Bt_scale = 50000f0)
```

Extract the matrix form of Tolles-Lawson coefficients from the vector form.

**Arguments:**

  * `TL_coef`:  Tolles-Lawson coefficients (must include `:permanent` & `:induced`)
  * `terms`:    Tolles-Lawson terms used {`:permanent`,`:induced`,`:eddy`}
  * `Bt_scale`: (optional) scaling factor for induced & eddy current terms [nT]

**Returns:**

  * `TL_coef_p`: length-`3` vector of permanent field coefficients
  * `TL_coef_i`: `3` x `3`  symmetric matrix of induced field coefficients, denormalized
  * `TL_coef_e`: `3` x `3`  matrix of eddy current coefficients, denormalized
