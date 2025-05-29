```julia
struct Flatten{T<:Integer} <: MIPVerify.Layer
```

Represents a flattening operation.

`p(x)` is shorthand for [`permute_and_flatten(x, p.perm)`](@ref) when `p` is an instance of `Flatten`.

## Fields:

  * `n_dim`
  * `perm`
