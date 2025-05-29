```
fugacity_coefficient(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

ファガシティ係数 φᵢ を計算します。これは次のように定義されます：

```julia
log(φᵢ) = μresᵢ/RT - log(Z)
```

ここで `μresᵢ` は残余化学ポテンシャルのベクトルであり、`Z` は圧縮率です。

内部的には、[`Clapeyron.volume`](@ref) を呼び出して `V` を取得し、`VT_fugacity_coefficient(model,V,T,z)` を介してプロパティを計算します。

キーワード `phase`、`threaded`、および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。
