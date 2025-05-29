```
scf_energy_force_stress(c::crystal; database = missing, smearing = 0.01, grid = missing)
```

Calculate energy, force, and stress for a crystal.

`return energy, force, stress, tight_binding_crystal_object`

# Arguments

  * `c::crystal`: the structure to calculate on. Only required argument.
  * `database=missing`: Source of coeficients. Will be loaded from pre-fit coefficients if missing.
  * `smearing=0.01`: Gaussian smearing temperature, in Ryd. Usually can leave as default.
  * `grid=missing`: k-point grid, e.g. [10,10,10], default chosen automatically
  * `sparse = :auto`: Default is to use dense matricies for `nat < 100`. Can be `true` or `false` to force choice.
