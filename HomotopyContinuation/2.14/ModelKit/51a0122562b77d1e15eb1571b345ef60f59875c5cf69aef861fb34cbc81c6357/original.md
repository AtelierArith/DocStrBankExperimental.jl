```
optimize(F::System)
```

Optimize the evaluation cost of the given system `F`. This applies a multivariate horner schema to the given expressions. See also [`horner`](@ref).

### Example

```julia
julia> f
System of length 4
 4 variables: z₁, z₂, z₃, z₄

 z₁ + z₂ + z₃ + z₄
 z₂*z₁ + z₂*z₃ + z₃*z₄ + z₄*z₁
 z₂*z₃*z₁ + z₂*z₃*z₄ + z₂*z₄*z₁ + z₃*z₄*z₁
 -1 + z₂*z₃*z₄*z₁

julia> optimize(f)
System of length 4
 4 variables: z₁, z₂, z₃, z₄

 z₁ + z₂ + z₃ + z₄
 (z₂ + z₄)*z₁ + (z₂ + z₄)*z₃
 z₁*(z₃*z₄ + (z₃ + z₄)*z₂) + z₂*z₃*z₄
 -1 + z₂*z₃*z₄*z₁
```
