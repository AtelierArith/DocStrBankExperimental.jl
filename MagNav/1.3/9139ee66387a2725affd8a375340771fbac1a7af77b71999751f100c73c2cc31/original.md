```
corrupt_mag(mag_c, Bx, By, Bz;
            dt           = 0.1,
            cor_sigma    = 1.0,
            cor_tau      = 600.0,
            cor_var      = 1.0^2,
            cor_drift    = 0.001,
            cor_perm_mag = 5.0,
            cor_ind_mag  = 5.0,
            cor_eddy_mag = 0.5)
```

Corrupt compensated (clean) magnetometer measurements with random, FOGM, drift, and Tolles-Lawson noise to create uncompensated (corrupted) scalar magnetometer measurements. FOGM is a First-order Gauss-Markov stochastic process.

**Arguments:**

  * `mag_c`:        compensated (clean) scalar magnetometer measurements [nT]
  * `Bx`,`By`,`Bz`: vector magnetometer measurements [nT]
  * `dt`:           (optional) measurement time step [s]
  * `cor_sigma`:    (optional) corruption FOGM catch-all bias [nT]
  * `cor_tau`:      (optional) corruption FOGM catch-all time constant [s]
  * `cor_var`:      (optional) corruption measurement (white) noise variance [nT^2]
  * `cor_drift`:    (optional) corruption measurement linear drift [nT/s]
  * `cor_perm_mag`: (optional) corruption permanent field TL coef std dev
  * `cor_ind_mag`:  (optional) corruption induced field TL coef std dev
  * `cor_eddy_mag`: (optional) corruption eddy current TL coef std dev

**Returns:**

  * `mag_uc`:   uncompensated (corrupted) scalar magnetometer measurements [nT]
  * `TL_coef`:  Tolles-Lawson coefficients (partially) used to create `mag_uc`
  * `cor_fogm`: corruption FOGM portion [nT]
