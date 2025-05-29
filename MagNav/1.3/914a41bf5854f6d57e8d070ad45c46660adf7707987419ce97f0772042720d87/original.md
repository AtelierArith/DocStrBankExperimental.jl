```
create_TL_A(flux::MagV, ind = trues(length(flux.x));
            Bt       = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
            terms    = [:permanent,:induced,:eddy],
            Bt_scale = 50000,
            return_B = false)
```

Create Tolles-Lawson `A` matrix using vector magnetometer measurements. Optionally returns the magnitude & derivatives of total field.

**Arguments:**

  * `flux`:     `MagV` vector magnetometer measurement struct
  * `ind`:      (optional) selected data indices
  * `Bt`:       (optional) magnitude of vector magnetometer measurements or scalar magnetometer measurements for modified Tolles-Lawson [nT]
  * `terms`:    (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`: (optional) scaling factor for induced & eddy current terms [nT]
  * `return_B`: (optional) if true, also return `Bt` & `B_dot`

**Returns:**

  * `A`:     Tolles-Lawson `A` matrix
  * `Bt`:    if `return_B = true`, magnitude of total field measurements [nT]
  * `B_dot`: if `return_B = true`, finite differences of total field vector [nT]
