```
inspectintegpoints(self::FEMMAcoust,
    geom::NodalField{GFT},
    P::NodalField{T},
    temp::NodalField{FT},
    felist::VecOrMat{IntT},
    inspector::F,
    idat,
    quantity = :gradient;
    context...) where {T <: Number, GFT, FT, IntT, F <: Function}
```

積分点の量を検査します。

# 引数

  * `geom` - 参照幾何フィールド
  * `P` - 圧力フィールド
  * `temp` - 温度フィールド（無視されます）
  * `felist` - 検査対象の有限要素のインデックス: 含まれるfesは次の通りです: `fes[felist]`。
  * `context` - 構造体: 材料のupdate!()メソッドを参照してください。
  * `inspector` - シグネチャを持つ関数 `idat = inspector(idat, j, conn, x, out, loc);` ここで `idat` - インスペクタが状態を維持するために使用する構造体または配列、例えば勾配、`j` は要素番号、`conn` は要素の接続、`out` は `update!()` メソッドの出力、`loc` は*参照*構成における積分点の位置です。

# 出力

更新されたインスペクタデータが返されます。
