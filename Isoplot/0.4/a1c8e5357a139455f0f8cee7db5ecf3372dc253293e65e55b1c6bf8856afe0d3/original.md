```
struct UPbAnalysis{T} <: NoInitialDaughterAnalysis{T}
```

Core type for U-Pb analyses. Wraps an Analysis object which has fields

```
μ :: SVector{T<:AbstractFloat}
σ :: SVector{T<:AbstractFloat}
Σ :: SMatrix{T<:AbstractFloat}
```

where `μ` contains the means

```
μ = [r²⁰⁷Pb²³⁵U, r²⁰⁶Pb²³⁸U]
```

where `σ` contains the standard deviations

```
σ = [σ²⁰⁷Pb²³⁵U, σ²⁰⁶Pb²³⁸U]
```

and Σ contains the covariance matrix

```
Σ = [σ₇_₅^2 σ₇_₅*σ₃_₈
     σ₇_₅*σ₃_₈ σ₃_₈^2]
```

If `σ` is not provided, it will be automatically calculated from `Σ`, given that `σ.^2 = diag(Σ)`.
