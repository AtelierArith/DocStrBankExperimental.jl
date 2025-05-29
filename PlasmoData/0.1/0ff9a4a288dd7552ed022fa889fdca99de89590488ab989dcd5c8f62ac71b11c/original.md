```
DataDiGraph{T, T1, T2, M1, M2}()
DataDiGraph()
```

Constructor for initializing and empty DataDiGraph object. Datatypes are as follows: T is the integer type for indexing, T1 and T2 are the data type in the node and edge data respectively, and M1 <: AbstractMatrix{T1} corresponds to the node data and M2 <: AbstractMatrix{T2} corresponds to the edge data.

When T, T1, T2, M1, and M2 are not defined, the defaults are `Int`, `Float64`, `Float64`, `Matrix{Float64}`, and `Matrix{Float64}` respectively.
