```
AutoFiniteDiff{T1,T2,T3}
```

Struct used to select the [FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl) backend for automatic differentiation.

Defined by [ADTypes.jl](https://github.com/SciML/ADTypes.jl).

# Constructors

```
AutoFiniteDiff(; fdtype=Val(:forward), fdjtype=fdtype, fdhtype=Val(:hcentral), relstep=nothing, absstep=nothing)
```

# Fields

  * `fdtype::T1`: finite difference type
  * `fdjtype::T2`: finite difference type for the Jacobian
  * `fdhtype::T3`: finite difference type for the Hessian
  * `relstep`: relative finite difference step size
  * `absstep`: absolute finite difference step size
  * `dir`: direction of the finite difference step
