```
create_TL_A(Bx, By, Bz;
            Bt       = sqrt.(Bx.^2+By.^2+Bz.^2),
            terms    = [:permanent,:induced,:eddy],
            Bt_scale = 50000,
            return_B = false)
```

Create Tolles-Lawson `A` matrix using vector magnetometer measurements. Optionally returns the magnitude & derivatives of total field.

**Arguments:**

  * `Bx`,`By`,`Bz`: vector magnetometer measurements [nT]
  * `Bt`:           (optional) magnitude of vector magnetometer measurements or scalar magnetometer measurements for modified Tolles-Lawson [nT]
  * `terms`:        (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `Bt_scale`:     (optional) scaling factor for induced & eddy current terms [nT]
  * `return_B`:     (optional) if true, also return `Bt` & `B_dot`

**Returns:**

  * `A`:     Tolles-Lawson `A` matrix
  * `Bt`:    if `return_B = true`, magnitude of total field measurements [nT]
  * `B_dot`: if `return_B = true`, finite differences of total field vector [nT]
