```
DGMultiMesh(dg::DGMulti{2, Tri}, triangulateIO, boundary_dict::Dict{Symbol, Int})
```

  * `dg::DGMulti` は、基準要素に関連する情報を含みます（例：数値積分、基底評価、微分など）。
  * `triangulateIO` は `TriangulateIO` メッシュ表現です。
  * `boundary_dict` は、各整数 `TriangulateIO` 境界タグを `Symbol` に関連付ける `Dict{Symbol, Int}` です。
