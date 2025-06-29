```
grad!(q::Edges{Primal},w::Nodes{Primal})
```

プライマルノードデータ `w` の離散勾配を評価し、それをプライマルエッジデータ `q` として返します。

# 例

```jldoctest
julia> w = Nodes(Primal,(8,6));

julia> w[3,4] = 1.0;

julia> q = Edges(Primal,(8,6));

julia> grad!(q,w)
Edges{Primal,8,6,Float64} data
u (グリッド方向)
5×8 Array{Float64,2}:
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  1.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0   0.0  0.0  0.0  0.0  0.0
v (グリッド方向)
6×7 Array{Float64,2}:
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0  -1.0  0.0  0.0  0.0  0.0
 0.0  0.0   1.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
 0.0  0.0   0.0  0.0  0.0  0.0  0.0
```
