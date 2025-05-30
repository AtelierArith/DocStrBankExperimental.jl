```
Mesh(graphs, Float64; parallel = false, message = nothing)
```

`Graph`オブジェクトの配列（`graphs`）からレンダリング用のメッシュを作成します。グラフはシリアル（デフォルト）またはマルチスレッドを使用して並列に処理できます（`parallel = true`）。デフォルトでは、倍精度浮動小数点（`Float64`）が使用されますが、`Mesh(graphs, Float32)`のように対応する型を指定することで、異なる精度のバージョンを生成することも可能です。
