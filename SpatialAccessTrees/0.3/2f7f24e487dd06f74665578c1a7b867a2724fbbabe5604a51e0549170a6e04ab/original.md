```
struct Sat{DT<:SemiMetric,DBT<:AbstractDatabase} <: AbstractSearchIndex
    dist::DT
    db::DBT
    root::UInt32
    # parents::Vector{UInt32}
    children::Vector{Union{Nothing,Vector{UInt32}}}
    cov::Vector{Float32} # leafs: ``- d(parent, leaf)``, internal: ``\max \{d(parent, u) | u \in children(parent)\}``
end
```

Spatial Access Tree data structure. Please see `Sat` function for high level constructors
