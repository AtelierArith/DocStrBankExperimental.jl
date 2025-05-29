```
FVMGeometry(tri::Triangulation)
```

これは、PDEのメッシュと関連データを保持する[`FVMGeometry`](@ref)構造体のコンストラクタです。

!!! note
    `tri`内のすべての頂点が三角形分割に含まれていると仮定されており、つまり`DelaunayTriangulation.each_point_index(tri)`の各`v`に対して`v`は`tri`に含まれています。


# フィールド

  * `triangulation`: DelaunayTriangulation.jlからの基礎となる`Triangulation`。
  * `triangulation_statistics`: 三角形分割の統計。
  * `cv_volumes::Vector{Float64}`: 各制御体積の体積の`Vector`。
  * `triangle_props::Dict{NTuple{3,Int},TriangleProperties}`: 各三角形のインデックスをその[`TriangleProperties`]にマッピングする`Dict`。
