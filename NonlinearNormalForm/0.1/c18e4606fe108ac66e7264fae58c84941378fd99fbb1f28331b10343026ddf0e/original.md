```
NonlinearNormalForm.DAMap(M::AbstractMatrix; use::UseType=GTPSA.desc_current, x0::Vector=zeros(eltype(M), size(M,1)), Q::Union{Quaternion,Nothing}=nothing, E::Union{Matrix,Nothing}=nothing, idpt::Union{Bool,Nothing}=nothing, spin::Union{Bool,Nothing}=nothing, FD::Union{Bool,Nothing}=nothing)
```

This function could be optimized.

`M` must represent a matrix with linear indexing.

Constructs a NonlinearNormalForm.DAMap with the passed matrix of scalars `M` as the linear part of the `TaylorMap`, and optionally the entrance  coordinates `x0`, `Quaternion` for spin `Q`, and FD matrix `E` as keyword arguments. The helper keyword  arguments `spin` and `FD` may be set to `true` to construct a NonlinearNormalForm.DAMap with an identity quaternion/FD  matrix, or `false` for no spin/FD. Note that setting `spin`/`FD` to any `Bool` value without `Q` or `E`  specified is type-unstable. This constructor also checks for consistency in the length of the orbital ray and GTPSA  `Descriptor`.
