```
vmag(V, grid, I...)
```

ベクトル場 `V` の大きさを、構造化グリッド `grid` の指定されたグリッド位置 `I` で計算します。

## 引数

  * `V`: 各成分が `AbstractField` であるベクトル場を表す名前付きタプル。
  * `grid`: ベクトル場が定義されている構造化グリッド。
  * `I...`: グリッド上の位置を指定するインデックス。
