```
relax_structure(c::crystal; mode="vc-relax")
```

Find the lowest energy atomic configuration of crystal `c`.

# Arguments

  * `c::crystal`: the structure to relax, only required argument
  * `mode="vc-relax"`: Default (variable-cell relax) will relax structure and cell, anything else will relax structure only.
  * `database=missing`: coefficent database, default is to use the pre-fit pbesol database
  * `smearing=0.01`: smearing temperature (ryd), default = 0.01
  * `grid=missing`: k-point grid, e.g. [10,10,10], default chosen automatically
  * `nsteps=100`: maximum iterations
  * `update_grid=true`: update automatic k-point grid during relaxation
  * `conv_thr = 2e-3`: Convergence threshold for gradient
  * `energy_conv_thr = 2e-4`: Convergence threshold for energy in Ryd
  * `sparse = :auto`: Default is to use dense matricies for `nat < 100`. Can be `true` or `false` to force choice.
