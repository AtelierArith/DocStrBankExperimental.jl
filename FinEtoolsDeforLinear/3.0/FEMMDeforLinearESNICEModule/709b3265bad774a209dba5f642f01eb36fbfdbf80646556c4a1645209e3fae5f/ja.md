```
inspectintegpoints(
    self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
    felist::Vector{IT},
    inspector::F,
    idat,
    quantity = :Cauchy;
    context...,
) where {FEMM<:AbstractFEMMDeforLinearESNICE,GFT<:Number,UFT<:Number,TFT<:Number,IT<:Integer,F<:Function}
```

統合点の量を検査します。

# 引数

  * `geom` - 参照幾何学フィールド
  * `u` - 変位フィールド
  * `dT` - 温度差フィールド
  * `felist` - 検査対象の有限要素のインデックス: 含めるfesは次の通りです: `fes[felist]`。
  * `context`    - 構造体: 材料のupdate!()メソッドを参照してください。
  * `inspector` - シグネチャidat = inspector(idat, j, conn, x, out, loc);を持つ関数; ここで`idat`は、検査官が状態を維持するために使用する構造体または配列であり、例えば応力の最小値または最大値、`j`は要素番号、`conn`は要素の接続性、`out`はupdate!()メソッドの出力、`loc`は*参照*構成における統合点の位置です。

# 戻り値

更新された検査官データが返されます。
