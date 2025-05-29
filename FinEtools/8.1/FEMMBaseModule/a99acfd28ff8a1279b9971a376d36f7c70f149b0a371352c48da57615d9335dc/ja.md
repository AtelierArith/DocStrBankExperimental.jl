```
elemfieldfromintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    quantity::Symbol,
    component::AbstractVector{IT};
    context...,
) where {FEMM<:AbstractFEMM, GFT<:Number, UFT<:Number, TFT<:Number, IT<:Integer}
```

積分点から要素場を構築します。

# 引数

`geom`     - 参照幾何場 `u`        - 変位場 `dT`       - 温度差場 `quantity`   - これは、材料の update!() メソッドの 'quantity' 引数に割り当てるものです。 `component`- 'quantity' 配列のコンポーネント: 材料の update() メソッドを参照してください。

# 出力

  * 値を色などにマッピングするために使用できる新しい場
