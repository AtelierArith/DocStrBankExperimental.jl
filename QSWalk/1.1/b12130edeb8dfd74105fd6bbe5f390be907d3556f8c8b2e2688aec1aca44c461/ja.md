```
type VertexSet
```

`Vertex`オブジェクトのリストからなる型です。これは線形部分空間の分割を記述します。この型のオブジェクトは、`make_vertex_set`または`nm_lind`関数を使用して構築する必要があります。`vertexset`型のオブジェクトから頂点のリストを取得するには、`vlist`関数を使用するか、特定の`Vertex`については、インデックス取得関数`vertexset[i]`を使用します。
