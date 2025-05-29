```
∂∂Bb!(::Model)
```

Returns up to second order partial derivatives with respect to `x`

## Default

  * None, must be supplied by the user.

## Remarks

  * Required for second order optimization techniques.
  * Returns `(B, b, ∂B, ∂b, ∂∂B, ∂∂b)::Tuple`
  * `(B, b, ∂B, ∂b)` as returned from [∂Bb!](@ref ∂Bb!)
  * Types: `∂∂B::SMatrix{Nx, Nx, SMatrix{Nc,Nc,T}}` and `∂∂b::SMatrix{Nx, Nx, SVector{Nc,T}}`
  * (or anything, which works with the implementation of [fgh!](@ref fgh!))
