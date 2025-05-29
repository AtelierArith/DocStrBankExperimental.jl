```julia
elementify(data::AbstractArray, [elements=data[1,:]];
    	importas=:Dict,
    	standardize::Bool=true,
    	floattype=Float64,
    	skipstart::Integer=1,
    	skipnameless::Bool=true
)
```

Convert a flat array `data` into a Named Tuple (`importas=:Tuple`) or Dictionary (`importas=:Dict`) with each column as a variable. Tuples are substantially more efficient, so should be favored where possible.

### Examples

```julia
julia> A = ["La" "Ce" "Pr"; 1.5 1.1 1.0; 3.7 2.9 2.5]
3×3 Matrix{Any}:
  "La"   "Ce"   "Pr"
 1.5    1.1    1.0
 3.7    2.9    2.5

julia> elementify(A, importas=:Tuple)
NamedTuple with 3 elements:
La  = Vector{Float64}(2,) [1.5 ... 3.7]
Ce  = Vector{Float64}(2,) [1.1 ... 2.9]
Pr  = Vector{Float64}(2,) [1.0 ... 2.5]

julia> elementify(A, importas=:Dict)
Dict{String, Union{Vector{Float64}, Vector{String}}} with 4 entries:
  "Ce"       => [1.1, 2.9]
  "Pr"       => [1.0, 2.5]
  "elements" => ["La", "Ce", "Pr"]
  "La"       => [1.5, 3.7]
```
