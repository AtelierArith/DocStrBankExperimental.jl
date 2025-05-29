sortnatural(x::Vector{String}) => Vector(::String)

Natural sort a string vector accounting for numeric sorting.

## Example

```julia
julia> myvec = ["12", "2", "1", "Y", "10", "X"];
julia> sort(myvec)
6-element Vector{String}:
 "1"
 "10"
 "12"
 "2"
 "X"
 "Y"
 julia> sortnatural(myvec)
 6-element Vector{String}:
  "1"
  "2"
  "10"
  "12"
  "X"
  "Y"
```
