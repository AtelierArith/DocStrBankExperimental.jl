```julia
mutable struct SIHSortStats
```

Useful stats saved after sorting.

# Methods

```
SIHSortStats(splitters, num_elements)
SIHSortStats(;splitters=nothing, num_elements=nothing)
```

# Fields

  * `splitters::Union{Nothing, Vector}`: Values used to split elements across MPI ranks, length=`nranks - 1` Default: nothing
  * `num_elements::Union{Nothing, Vector{Int64}}`: Number of elements saved locally to each MPI rank, length=`nranks`. Default: nothing
