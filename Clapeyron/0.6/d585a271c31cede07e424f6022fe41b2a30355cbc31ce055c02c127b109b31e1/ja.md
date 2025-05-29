```
isobaric_expansivity(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[K^-1]`

定義された等圧膨張率を計算します:

```julia
α = -∂²A/∂V∂T / (V*∂²A/∂V²)
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_isobaric_expansivity(model,V,T,z)`を介してプロパティを計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
