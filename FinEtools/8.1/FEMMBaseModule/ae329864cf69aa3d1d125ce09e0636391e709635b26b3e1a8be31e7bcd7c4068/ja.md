```
fieldfromintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    quantity::Symbol,
    component::AbstractVector{IT};
    context...,
) where {FEMM<:AbstractFEMM, GFT<:Number, UFT<:Number, TFT<:Number, IT<:Integer}
```

積分点からノードフィールドを構築します。

# 引数

  * `geom`     - 参照幾何フィールド
  * `u`        - 変位フィールド
  * `dT`       - 温度差フィールド
  * `quantity`   - これは、material update!() メソッドの 'quantity' 引数に割り当てるものです。
  * `component`- 'quantity' 配列のコンポーネント: material update() メソッドを参照してください。

キーワード引数

  * `nodevalmethod` = `:invdistance`（デフォルト）または `:averaging`；
  * `reportat` = 要素の量が報告されるべきポイントはどこですか？ この引数は `inspectintegpoints()` メソッド内で解釈されます。

# 出力

  * 値を色などにマッピングするために使用できる新しいフィールド
