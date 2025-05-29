```
export_gml(fpn::String, G::AbstractGraph{::Integer}, kwargs...)
```

グラフ `G` を .gml ファイルとして保存します。

`G` は `FlipGraph` または `FlipGraphPlanar` のいずれかです。

# 引数

  * vertex_attributes::Vector{Dict} : 提供される場合、`i` 番目の頂点は `i` 番目の `Dict` から属性を取得します。                                    各 `key`, `value` ペアは属性を定義し、`key` は属性の名前、`value` はその値です。
  * edge_attributes::Vector{Dict}   : 提供される場合、`i` 番目の辺は `i` 番目の `Dict` から属性を取得します。                                    各 `key`, `value` ペアは属性を定義し、`key` は属性の名前、`value` はその値です。
  * add_diameter = false :            true に設定すると、エクスポートされた木のすべての頂点に、その頂点の `DeltaComplex` のそれぞれの直径を持つ diameter という属性が付与されます。

# 例

```julia-repl
julia> G = flipgraph_planar(10);
julia> export_gml("C:/Users/USERNAME/Desktop/filename.gml", G);
```

追加のシンボル `:diameter` を加えることで、ノードはモデル化する `DeltaComplex` または `TriangulatedPolygon` の直径に対応する値 *diameter* を取得します。ただし、この直径は実行時に計算されるため、このエクスポートメソッドは大幅に遅くなることに注意してください。

```julia-repl
julia> G = flipgraph_modular(1,3,labeled_points = true);
julia> export_gml("C:/Users/USERNAME/Desktop/filename.gml", G, add_diameter=true);
```
