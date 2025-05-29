```julia
GetBZPath(bz::BZ, start::Vector{Float64}, ending::Vector{Float64} ; nearest::Bool = false, exclusive::Bool = true) --> Vector{Vector{Float64}}
```

Returns the actual path in momentum-space of the discretized `BZ` which joins the two momentums `start` and `ending`.  The optional input `nearest` is the same as in [`GetQIndex`](@ref), and `exclusive` is the same as in [`GetIndexPath`](@ref).
