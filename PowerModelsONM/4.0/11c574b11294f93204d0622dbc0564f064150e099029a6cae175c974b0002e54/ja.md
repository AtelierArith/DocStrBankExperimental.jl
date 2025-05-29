```
NestedGraph <: InfrastructureGraph
```

ネストされたグラフ構造で、属性は次のとおりです。

```julia
node::Dict{String,UnnestedGraph}
edge::Vector{Dict{String,String}}
```
