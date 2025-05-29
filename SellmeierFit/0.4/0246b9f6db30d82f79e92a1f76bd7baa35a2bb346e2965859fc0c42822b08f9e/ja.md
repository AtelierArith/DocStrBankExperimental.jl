```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}; λmin::Real=-Inf, λmax::Real=Inf, Nmax::Integer=10, rtol_λres::Real=1e-3)
```

波長 `λ` でサンプリングされた誘電率データ `ε` を、最大 `Nmax` 項のセールマイヤー方程式にフィットさせます。 `λmin` と `λmax` の間の `λ` のエントリと対応する `ε` のエントリのみが使用されます。 異なる項の `λres` の相対差が `rtol_λres` より小さい場合、それらは同じ項と見なされ、統合されます。
