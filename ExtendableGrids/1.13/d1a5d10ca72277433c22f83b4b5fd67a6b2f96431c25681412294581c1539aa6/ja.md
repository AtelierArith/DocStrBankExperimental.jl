```
function simplexgrid(coord::Array{Tc,2},
                     cellnodes::Array{Ti,2},
                     cellregions=ones(Ti, size(coord,2)),
                     bfacenodes=zeros(Ti,size(coord,1),0),
                     bfaceregions=zeros(Ti,length(bfacenodes))
                     ) where {Tc,Ti}
```

d次元単純体グリッドを5つの配列から作成します。

  * ```
       coord: d ``\times`` n_points の座標行列
    ```
  * cellnodes: d+1 $\times$ n_tri の三角形 - 点の発生
  * cellregions: (オプション) n_tri のセル領域マーカーのベクトル
  * bfacenodes: (オプション) d $\times$ n_bf の境界ファセット - 点の発生
  * bfaceregions: (オプション) n_bf の境界ファセット領域マーカーのベクトル

座標型 `Tc` インデックス型 `Ti` は最初の2つのパラメータから検出されます。 `cellregions`、`bfaceregions`、`bfacenodes` は `cellnodes` と同じ要素型を持つように変換されます。
