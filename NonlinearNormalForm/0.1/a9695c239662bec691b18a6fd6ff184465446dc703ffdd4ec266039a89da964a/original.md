```
NonlinearNormalForm.TPSAMap(;use::UseType=GTPSA.desc_current, x::Vector=vars(getdesc(use)), x0::Vector=zeros(eltype(eltype(x)), numvars(use)), Q::Union{Quaternion,Nothing}=nothing, E::Union{Matrix,Nothing}=nothing, idpt::Union{Bool,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing, FD::Union{Bool,Nothing}=nothing)
```

Constructs a NonlinearNormalForm.TPSAMap with the passed vector of `TPS`/`ComplexTPS64` as the orbital ray, and optionally the entrance  coordinates `x0`, `Quaternion` for spin `Q`, and FD matrix `E` as keyword arguments. The helper keyword  arguments `spin` and `FD` may be set to `true` to construct a NonlinearNormalForm.TPSAMap with an identity quaternion/FD  matrix, or `false` for no spin/FD. Note that setting `spin`/`FD` to any `Bool` value without `Q` or `E`  specified is type-unstable. This constructor also checks for consistency in the length of the orbital ray and GTPSA  `Descriptor`. The `use` kwarg may also be used to change the `Descriptor` of the TPSs, provided the number of variables 

  * parameters agree (orders may be different).
