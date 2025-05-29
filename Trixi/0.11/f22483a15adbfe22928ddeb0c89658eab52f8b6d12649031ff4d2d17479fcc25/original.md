```
DGMultiBasis(element_type, polydeg; approximation_type = Polynomial(), kwargs...)
```

Constructs a basis for DGMulti solvers. Returns a "StartUpDG.RefElemData" object.   The `kwargs` arguments are additional keyword arguments for `RefElemData`, such as `quad_rule_vol`.   These are the same as the `RefElemData_kwargs` used in [`DGMulti`](@ref).   For more info, see the [StartUpDG.jl docs](https://jlchan.github.io/StartUpDG.jl/dev/).
