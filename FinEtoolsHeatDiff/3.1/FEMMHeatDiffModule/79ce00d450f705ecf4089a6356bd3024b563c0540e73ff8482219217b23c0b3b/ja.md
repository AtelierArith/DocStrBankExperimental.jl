```
inspectintegpoints(self::FEMMHeatDiff, geom::NodalField{GFT}, u::NodalField{T}, temp::NodalField{FT}, felist::VecOrMat{IntT}, inspector::F, idat, quantity=:heatflux; context...) where {T<:Number, GFT, FT, IntT, F<:Function}
```

積分点の量を検査します。

# 引数

  * `geom` - 参照幾何フィールド
  * `u` - 変位フィールド（無視されます）
  * `temp` - 温度フィールド
  * `felist` - 検査対象の有限要素のインデックス: 含める有限要素は `fes[felist]` です。
  * `context` - 構造体: 材料の `update!()` メソッドを参照してください。
  * `inspector` - シグネチャ `idat = inspector(idat, j, conn, x, out, loc);` を持つ関数。ここで、`idat` はインスペクタが状態を維持するために使用する構造体または配列で、例えば熱流、`j` は要素番号、`conn` は要素の接続性、`out` は `update!()` メソッドの出力、`loc` は *参照* 構成における積分点の位置です。

# 出力

更新されたインスペクタデータが返されます。
