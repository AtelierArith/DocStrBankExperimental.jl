```
isothermal_compressibility(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[Pa^-1]`

等温圧縮率を計算します。これは次のように定義されます:

```julia
κT = -(V*∂p/∂V)^-1
```

内部的には、[`Clapeyron.volume`](@ref)を呼び出して`V`を取得し、`VT_isothermal_compressibility(model,V,T,z)`を介して特性を計算します。

キーワード`phase`、`threaded`、および`vol0`は、[`Clapeyron.volume`](@ref)ソルバーに渡されます。
