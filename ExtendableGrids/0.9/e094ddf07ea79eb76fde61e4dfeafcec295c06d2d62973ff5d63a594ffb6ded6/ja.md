```
function simplexgrid(coord::Array{Tc,2},
                     cellnodes::Array{Ti,2},
                     cellregions,
                     bfacenodes,
                     bfaceregions,
                     bedgenodes,
                     bedgeregions
                     ) where {Tc,Ti}
```

座標、セルノードの隣接関係、セル領域番号、境界面ノードの隣接関係、境界面領域番号、境界エッジノード、および境界エッジ領域番号の配列から単純格子を作成します。

インデックスタイプ `Ti` は `cellnodes` から検出され、`coord` 以外のすべての配列はこのインデックスタイプに変換されます。
