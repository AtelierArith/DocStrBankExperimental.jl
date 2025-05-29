```
bipartite_map(g) -> Vector{UInt8}
```

二部グラフ `g` に対して、各頂点を二つの集合のいずれかに割り当てたサイズ $|V|$ のベクトル `c` を返します（$c_i == 1$ または $c_i == 2$）。もし `g` が二部グラフでない場合は、空のベクトルを返します。

### 実装ノート

空のベクトルは必ずしも非二部性を示すわけではないことに注意してください。空のグラフは空のベクトルを返しますが、二部グラフです。

# 例

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3);

julia> bipartite_map(g)
3-element Vector{UInt8}:
 0x01
 0x01
 0x01

julia> add_vertices!(g, 3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> bipartite_map(g)
6-element Vector{UInt8}:
 0x01
 0x02
 0x01
 0x01
 0x01
 0x01
```
