```
implied_conditional_independencies(dag)
```

From given DAG find all pair-wise conditional independencies of nodes. Returns vector of `ConditionalIndependence` structures.

# Examples

```jldoctest
julia> using Dagitty

julia> g = DAG(:A => :C, :C => :B)
DAG: {3, 2} directed simple Int64 graph with labels [:A, :B, :C])

julia> implied_conditional_independencies(g)
1-element Vector{ConditionalIndependence}:
 ConditionalIndependence(:A, :B, [:C])
```
