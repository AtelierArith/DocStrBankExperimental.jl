```
zero(G)
```

グラフタイプ `G` のゼロ頂点、ゼロエッジバージョンを返します。フォールバックはグラフ値 `zero(g::G) = zero(G)` として定義されています。

# 例

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> zero(typeof(g))
{0, 0} directed simple Int64 graph

julia> zero(g)
{0, 0} directed simple Int64 graph
```
