```
hodge(ω)
```

Hodge decomposition of a [`Cochain`](@ref) using [`inner`](@ref) as the inner product.

Return a tuple `(α,β,γ)` such that

```
ω == coboundary(α) + coboundary_adj(β) + γ
laplacian(γ) == 0
```
