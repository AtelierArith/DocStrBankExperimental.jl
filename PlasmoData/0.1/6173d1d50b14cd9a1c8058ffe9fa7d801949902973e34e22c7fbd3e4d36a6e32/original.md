```
DataGraph{T, T1, T2, T3, M1, M2}()
DataGraph()
```

Constructor for initializing and empty DataGraph object. Datatypes are as follows: T is the integer type for indexing, T1, T2, and T3 are the data type in the node, edge, and graph data respectively, and M1 <: AbstractMatrix{T1} corresponds to the node data and M2 <: AbstractMatrix{T2} corresponds to the edge data.

When T, T1, T2, T3, M1, and M2 are not defined, the defaults are `Int`, `Float64`, `Float64`, `Float64`, `Matrix{Float64}`, and `Matrix{Float64}` respectively.
