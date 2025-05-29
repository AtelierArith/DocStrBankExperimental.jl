```
χNMatrix(m)
```

Convert a dictionary of interaction pairs to an interaction matrix. The input argument `m` can be a dictionary of `Dict{Tuple{Symobl}, <:Real}`, `Dict{Tuple{String}, <:Real}`, `Dict{<:AbstractArray{Symbol}, <:Real}`, `Dict{<:AbstractArray{String}, <:Real}`.

Example:

```julia
map = Dict((:A, :B)=>10.0, (:A, :C)=>20.0, (:B, :C)=>30.0)
map = Dict(("A", "B")=>10.0, ("A", "C")=>20.0, ("B", "C")=>30.0)
map = Dict([:A, :B]=>10, [:A, :C]=>10.0, [:B, :C]=>20.0)
map = Dict(["A", "B"]=>10.0, ["A", "C"]=>20.0, ["B", "C"]=>30.0)
```
