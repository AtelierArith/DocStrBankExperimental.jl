```
scale_coefficients!(F::AbstractSystem{T, M}, λ::AbstractVector)
```

Scale the coefficients of the polynomials `fᵢ` of `F` by the factor `λᵢ`. `λ` needs to have have length `M`.
