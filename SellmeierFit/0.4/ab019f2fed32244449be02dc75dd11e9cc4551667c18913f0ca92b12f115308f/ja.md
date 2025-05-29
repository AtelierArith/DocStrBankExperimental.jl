```
fit_sellmeier(λ::AbstractVector{<:Real}, ε::AbstractVector{<:Real}, Nₙ::Integer, Nₚ::Integer; λmin::Real=-Inf, λmax::Real=Inf)
```

波長 `λ` でサンプリングされた誘電率データ `ε` を、範囲 `λ` の下に正確に `Nₙ` 項、上に `Nₚ` 項を持つセルメイヤー方程式にフィットさせます。 `λmin` と `λmax` の間の `λ` のエントリと対応する `ε` のエントリのみが使用されます。
