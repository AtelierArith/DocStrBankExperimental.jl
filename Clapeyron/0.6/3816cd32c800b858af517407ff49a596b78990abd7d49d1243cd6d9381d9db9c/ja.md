```
speed_of_sound(model::EoSModel, p, T, z=SA[1.]; phase=:unknown, threaded=true, vol0=nothing)
```

デフォルト単位: `[m/s]`

音速を計算します。音速は次のように定義されます：

```julia
c = V * √(∂²A/∂V² - ∂²A/∂V∂T^2 / ∂²A/∂T²)/Mr)
```

ここで `Mr` は入力組成におけるモデルの分子量です。

内部的には、[`Clapeyron.volume`](@ref) を呼び出して `V` を取得し、`VT_speed_of_sound(model,V,T,z)` を介して特性を計算します。

キーワード `phase`、`threaded`、および `vol0` は [`Clapeyron.volume`](@ref) ソルバーに渡されます。

!!! warning "正確な理想モデルが必要"
    この特性には、少なくとも二次の理想モデル温度導関数が必要です。これらの特性を計算している場合は、デフォルトの `BasicIdeal` よりも異なる理想モデル（例: `EoS(["species"];idealmodel = ReidIdeal)`）を使用することを検討してください。

