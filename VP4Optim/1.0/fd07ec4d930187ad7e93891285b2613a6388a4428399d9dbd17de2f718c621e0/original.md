```
∂Bb!(::Model)
```

Returns up to first order partial derivatives with respect to `x`.

## Default

  * None, must be supplied by the user.

## Remarks

  * Required for first and second order optimization techniques.
  * Returns `(B, b, ∂B, ∂b)::Tuple`
  * `(B, b)` as returned from [Bb!](@ref Bb!)
  * Types: `∂B::SVector{Nx, SMatrix{Nc,Nc,T}}` and `∂b::SVector{Nx, SVector{Nc,T}}`
  * (or anything, which works with the implementation of [fg!](@ref) and [fgh!](@ref fgh!))
