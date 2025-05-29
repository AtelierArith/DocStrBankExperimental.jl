```
cycle_basis(g, root=nothing)
```

無向グラフ `g` のサイクルの基底を形成するサイクルのリストを返します。オプションでノード `root` から始めることができます。

ネットワークのサイクルの基底は、ネットワーク内の任意のサイクルが基底内のサイクルの和として書かれるような最小のサイクルのコレクションです。ここで、サイクルの和はエッジの「排他的論理和」として定義されます。サイクル基底は、キルヒホッフの法則を使用して電気回路の方程式を導出する際などに便利です。

# 例

```jldoctest
julia> using Graphs

julia> elist = [(1,2),(2,3),(2,4),(3,4),(4,1),(1,5)];

julia> g = SimpleGraph(Graphs.SimpleEdge.(elist));

julia> cycle_basis(g)
2-element Vector{Vector{Int64}}:
 [2, 4, 1]
 [2, 3, 4]
```

### 参考文献

  * Paton, K. グラフの基本的なサイクル集合を見つけるためのアルゴリズム。Comm. ACM 12, 9 (1969年9月), 514-518. [https://dl.acm.org/citation.cfm?id=363232]
