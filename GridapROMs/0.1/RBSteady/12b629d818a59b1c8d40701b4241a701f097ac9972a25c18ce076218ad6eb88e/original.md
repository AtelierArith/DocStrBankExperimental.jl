```
orth_projection(v::AbstractVector, basis::AbstractMatrix, args...) -> AbstractVector
```

Orthogonal projection of `v` on the column space of `basis`. When a symmetric, positive definite matrix `X` is provided as an argument, the output is `X`-orthogonal, otherwise it is ℓ²-orthogonal
