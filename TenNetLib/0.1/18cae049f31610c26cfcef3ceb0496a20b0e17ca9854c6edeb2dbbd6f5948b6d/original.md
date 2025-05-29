```
function indexintersection(inds1::Vector{Index}, inds2::Vector{Index};
                           maxdim::Union{Nothing, Int} = nothing,
                           maxqnblocks::Union{Nothing, Int} = nothing,
                           kwargs...)
```

Performs set intersection of two vectors of `Index`. `maxdim` is be the maximum dimension of the output `Index`, `maxqnblocks` represents maximum number of QN blocks to retain in the output `Index`.
