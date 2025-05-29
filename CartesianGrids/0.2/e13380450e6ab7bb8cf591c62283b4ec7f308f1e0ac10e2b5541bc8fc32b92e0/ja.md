```
divergence(q::Edges) --> Nodes
```

エッジデータ `q` の離散的発散を評価します。この操作は、Divergence型のオブジェクトを作成し、`*` で適用することでも実行できます。

# 例

```jldoctest
julia> D = Divergence();

julia> q = Edges(Primal,(8,6));

julia> q.u[3,2] = 1.0;

julia> D*q
Nodes{Primal,8,6,Float64} data
Printing in grid orientation (lower left is (1,1))
5×7 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  1.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
```
