```julia
SparseHamiltonian(funcs, mats; unit, dimensionless_time)

```

Constructor of the `SparseHamiltonian` type. `funcs` and `mats` are lists of time-dependent functions and the corresponding matrices. The Hamiltonian can be represented as $∑ᵢfuncs[i](s)×mats[i]$. `unit` specifies wether `:h` or `:ħ` is set to one when defining `funcs` and `mats`. The `mats` will be scaled by $2π$ if unit is `:h`.
