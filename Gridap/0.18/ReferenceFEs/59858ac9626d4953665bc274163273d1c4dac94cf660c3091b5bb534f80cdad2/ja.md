```
abstract type Polytope{D} <: GridapType
```

ポリトープを表す抽象型（すなわち、任意の次元の多面体）。`D`は環境の次元（通常は0、1、2、または3）です。この型パラメータは、`Polytope`インターフェースにおいて`Point{D}`オブジェクトを含むコンテナを返す関数があるため必要です。ポリトープ関連のオブジェクトには[通常の命名法](https://en.wikipedia.org/wiki/Polytope)を採用します。ポリトープ内のすべてのオブジェクト（頂点からポリトープ自体まで）は*n-面*または単に*面*と呼ばれます。*n-面*という表記は、オブジェクトの次元nを参照する必要がある場合にのみ使用されます。それ以外の場合は単に*面*を使用します。さらに、次のように言います。

  * 頂点（複数形：頂点）：0-面の場合
  * 辺：1-面の場合
  * 面：(`D-1`)-面の場合

`Polytope`インターフェースは、次の関数をオーバーロードすることによって定義されます。

  * [`get_faces(p::Polytope)`](@ref)
  * [`get_dimranges(p::Polytope)`](@ref)
  * [`Polytope{N}(p::Polytope,faceid::Integer) where N`](@ref)
  * [`get_vertex_coordinates(p::Polytope)`](@ref)
  * [`(==)(a::Polytope{D},b::Polytope{D}) where D`](@ref)

オプションで次の関数もあります。

  * [`get_edge_tangent(p::Polytope)`](@ref)
  * [`get_facet_normal(p::Polytope)`](@ref)
  * [`get_facet_orientations(p::Polytope)`](@ref)
  * [`get_vertex_permutations(p::Polytope)`](@ref)
  * [`is_n_cube(p::Polytope)`](@ref)
  * [`is_simplex(p::Polytope)`](@ref)
  * [`simplexify(p::Polytope)`](@ref)

インターフェースは次の関数でテストできます。

  * [`test_polytope`](@ref)
