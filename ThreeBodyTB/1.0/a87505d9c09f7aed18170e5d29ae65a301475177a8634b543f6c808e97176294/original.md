```
scf_energy(c::crystal)
```

Calculate energy, force, and stress for a crystal. Does self-consistent-field (SCF) calculation if using self-consistent electrostatics.

returns energy, tight-binding-crystal-object, error-flag

# Arguments

  * `c::crystal`: the structure to calculate on. Only required argument.
  * `database=missing`: Source of coeficients. Will be loaded from pre-fit coefficients if missing.
  * `smearing=0.01`: Gaussian smearing temperature, in Ryd. Usually can leave as default.
  * `grid=missing`: k-point grid, e.g. [10,10,10], default chosen automatically
  * `conv_thr = 1e-5`: SCF convergence threshold (Ryd).
  * `sparse = :auto`: Default is to use dense matricies for `nat < 100`. Can be `true` or `false` to force choice.
  * `iter = 75`: number of iterations before switch to more conservative settings.
  * `mix = -1.0`: initial mixing. -1.0 means use default mixing. Will automagically adjust mixing if SCF is failing to converge. Starting default is smaller for larger unit cells.
  * `mixing_mode = :simple`: default is simple. Other options are `:simple` and `:DIIS` / `:pulay` (direct inversion of iterative subspace). Will automatically switch to simple if Pulay fails.
