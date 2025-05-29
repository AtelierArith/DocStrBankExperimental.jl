```
hodge(ω)
```

[`Cochain`](@ref)を内積として[`inner`](@ref)を使用してのホッジ分解。

次のタプル `(α,β,γ)` を返します。

```
ω == coboundary(α) + coboundary_adj(β) + γ
laplacian(γ) == 0
```
