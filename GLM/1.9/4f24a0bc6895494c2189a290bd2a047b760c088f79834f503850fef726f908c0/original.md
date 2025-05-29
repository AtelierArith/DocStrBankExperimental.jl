```
PowerLink
```

A [`Link`](@ref) defined as `η = μ^λ` when `λ ≠ 0`, and to `η = log(μ)` when `λ = 0`, i.e. the class of transforms that use a power function or logarithmic function.

Many other links are special cases of `PowerLink`:

  * [`IdentityLink`](@ref) when λ = 1.
  * [`SqrtLink`](@ref) when λ = 0.5.
  * [`LogLink`](@ref) when λ = 0.
  * [`InverseLink`](@ref) when λ = -1.
  * [`InverseSquareLink`](@ref) when λ = -2.
