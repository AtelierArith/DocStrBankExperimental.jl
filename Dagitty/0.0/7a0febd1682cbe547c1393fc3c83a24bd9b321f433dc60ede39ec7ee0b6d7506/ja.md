```
implied_conditional_independencies(dag)
```

与えられたDAGからノードのすべてのペアワイズ条件独立性を見つけます。`ConditionalIndependence`構造体のベクターを返します。

# 例

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> implied_conditional_independencies(g)
1-element Vector{ConditionalIndependence}:
 ConditionalIndependence(:A, :B, [:C])
```
