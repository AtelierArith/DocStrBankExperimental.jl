```julia
unelementify(dataset, elements;
    	floatout::Bool=false,
    	floattype=Float64,
    	findnumeric::Bool=false,
    	skipnan::Bool=false,
    	rows=:
)
```

Convert a Dict or Named Tuple of vectors into a 2-D array with variables as columns

### Examples

```julia
julia> D
NamedTuple with 3 elements:
  La  = Vector{Float64}(2,) [1.5 ... 3.7]
  Ce  = Vector{Float64}(2,) [1.1 ... 2.9]
  Pr  = Vector{Float64}(2,) [1.0 ... 2.5]

julia> unelementify(D)
3×3 Matrix{Any}:
  "La"   "Ce"   "Pr"
 1.5    1.1    1.0
 3.7    2.9    2.5
```
