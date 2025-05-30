```
divergence!(w::Nodes,q::Edges)
```

エッジデータ `q` の離散的なダイバージェンスを評価し、それをノードデータ `w` として返します。`q` はプライマルまたはデュアルエッジデータのいずれかである可能性がありますが、`w` は同じセルタイプでなければなりません。

# 例

```jldoctest
julia> q = Edges(Primal,(8,6));

julia> q.u[3,2] = 1.0;

julia> w = Nodes(Primal,(8,6));

julia> divergence!(w,q)
Nodes{Primal,8,6,Float64} data
Printing in grid orientation (lower left is (1,1))
5×7 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  1.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
```
