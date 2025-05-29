```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}, N::Integer; λmin::Real=-Inf, λmax::Real=Inf)
```

波長 `λ` でサンプリングされた誘電率データ `ε` を、正確に `N` 項のセルメイヤー方程式にフィットさせます。 `λmin` と `λmax` の間の `λ` のエントリと対応する `ε` のエントリのみが使用されます。 `N` 項の中には、範囲 `λ` より下のものと上のものがあります。
