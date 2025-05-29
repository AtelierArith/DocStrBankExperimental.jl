```
DGMultiMesh(dg::DGMulti{NDIMS}, vertex_coordinates, EToV;
            is_on_boundary=nothing,
            periodicity=ntuple(_->false, NDIMS)) where {NDIMS}
```

  * `dg::DGMulti` は、参照要素に関連する情報（例：数値積分、基底評価、微分など）を含みます。
  * `vertex_coordinates` は、頂点座標の x,y,... 成分を含むベクトルのタプルです。
  * `EToV` は、各要素の要素-頂点接続を含む 2D 配列です。
  * `is_on_boundary` は、`Dict{Symbol, <:Function}` を使用して境界を指定します。
  * `periodicity` は、ドメインが (x,y,z) 方向で周期的かどうかを指定するブール値のタプルです。
