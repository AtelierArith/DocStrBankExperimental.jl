```
create_TL_coef(flux::MagV, B, ind = trues(length(flux.x));
               Bt         = sqrt.(flux.x.^2+flux.y.^2+flux.z.^2)[ind],
               λ          = 0,
               terms      = [:permanent,:induced,:eddy],
               pass1      = 0.1,
               pass2      = 0.9,
               fs         = 10.0,
               pole::Int  = 4,
               trim::Int  = 20,
               Bt_scale   = 50000,
               return_var = false)
```

Create Tolles-Lawson coefficients using vector & scalar magnetometer measurements with a bandpass, low-pass, or high-pass filter.

**Arguments:**

  * `flux`:       `MagV` vector magnetometer measurement struct
  * `B`:          scalar magnetometer measurements [nT]
  * `ind`:        (optional) selected data indices
  * `Bt`:         (optional) magnitude of vector magnetometer measurements or scalar magnetometer measurements for modified Tolles-Lawson [nT]
  * `λ`:          (optional) ridge parameter
  * `terms`:      (optional) Tolles-Lawson terms to use {`:permanent`,`:induced`,`:eddy`,`:bias`}
  * `pass1`:      (optional) first passband frequency [Hz]
  * `pass2`:      (optional) second passband frequency [Hz]
  * `fs`:         (optional) sampling frequency [Hz]
  * `pole`:       (optional) number of poles for Butterworth filter
  * `trim`:       (optional) number of elements to trim after filtering
  * `Bt_scale`:   (optional) scaling factor for induced & eddy current terms [nT]
  * `return_var`: (optional) if true, also return `B_var`

**Returns:**

  * `coef`:  Tolles-Lawson coefficients
  * `B_var`: if `return_var = true`, fit error variance
