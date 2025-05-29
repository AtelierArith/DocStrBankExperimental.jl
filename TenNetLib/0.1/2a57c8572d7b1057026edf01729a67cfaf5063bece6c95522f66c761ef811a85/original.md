```
function combineinds(inds::Vector{Index};
                     maxdim::Union{Nothing, Int} = nothing, 
                     maxqnblocks::Union{Nothing, Int} = nothing,
                     kwargs...)
```

Combine a vector of `Index` into one (like ITensors.jl's `combiner`). `maxdim` is be the maximum dimension of the output `Index`, `maxqnblocks` represents maximum number of QN blocks to retain in the output `Index`.
