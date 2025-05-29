```julia
DenseHamiltonian(funcs, mats; unit, dimensionless_time)

```

Constructor of the `DenseHamiltonian` type. `funcs` and `mats` are lists of time-dependent functions and the corresponding matrices. The Hamiltonian can be represented as $∑ᵢfuncs[i](s)×mats[i]$. 

`unit` specifies wether `:h` or `:ħ` is set to one when defining `funcs` and `mats`. The `mats` will be scaled by $2π$ if unit is `:h`.

`dimensionless_time` specifies wether the arguments of the functions are dimensionless (normalized to total evolution time).
