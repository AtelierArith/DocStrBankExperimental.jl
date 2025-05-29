```
abstract type AbstractInstance
```

The required interface for external data to be provided to the decoder. The problem definitions and data **must be** a subtype of AbstractInstance. For example,

```julia
mutable struct TSPInstance <: AbstractInstance
    num_cities::Int64
    distances::Array{Float64}
end
```

represents an instance type for the Traveling Salesman problem which defines the number fo cities and a matrix of distances between them.
