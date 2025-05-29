```julia
CombinedIndexPath(bz::BZ, points::Vector{Vector{Float64}} ; nearest::Bool = false, closed::Bool = true) --> Vector{Vector{Int64}}
```

Returns a path in index-space joins the given points present in `points` as point[1] –> point[2] –> ... –> point[end] –> point[1]. The optional input `nearest` is the same as in [`GetQIndex`](@ref), and `closed` determines if the path is a closed loop or not.
