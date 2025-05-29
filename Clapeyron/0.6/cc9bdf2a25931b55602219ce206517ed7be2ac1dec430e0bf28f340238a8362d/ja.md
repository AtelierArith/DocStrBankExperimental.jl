```
compressibility_factor(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

圧縮率 `Z` を計算します。定義は次の通りです：

```julia
Z = p*V(p)/R*T
```

キーワード `phase`、`threaded`、および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
