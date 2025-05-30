```
Mesh(graphs, Float64; parallel = false, message = nothing)
```

`Graph`オブジェクトの配列（`graphs`）からレンダリング用のメッシュを作成します。グラフはシリアルに処理される（デフォルト）か、マルチスレッドを使用して並列に処理されることができます（`parallel = true`）。デフォルトでは、倍精度浮動小数点数が使用されます（`Float64`）が、対応する型を指定することで異なる精度のバージョンを生成することも可能です（`Mesh(graphs, Float32)`のように）。
