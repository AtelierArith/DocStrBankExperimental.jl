```
UnnestedGraph <: InfrastructureGraph
```

アンネストされたグラフ構造で、属性は次のとおりです。

```julia
node::Vector{Pair{String,Dict{String,String}}}
edge::Vector{Dict{String,String}}
```
