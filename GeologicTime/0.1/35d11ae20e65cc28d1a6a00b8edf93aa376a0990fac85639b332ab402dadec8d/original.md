```
getgeotime(millionyears::Real, unit::Integer; bound=:forward) :: 
	Union{String, Nothing}
getgeotime(millionyears::Real; bound=:forward) :: 
	Vector{Pair{String, String}}
```

Find the geologic time of a certain `unit` containing the given time moment  (in million year). 

The argument `unit` must be `1` (eon), `2` (era), `3` (period), `4` (epoch),  or `5` (age); `bound` must be `:forward` (default) or `:backward`. When `unit`  is omitted, results of all possible units are packed up and returned.

When no geologic time contains the given time moment, `nothing` is returned  if `unit` is specified, or the result is simply omitted in the returned vector. 

# Example

```jldoctest
julia> getgeotime(39, 3)
"Paleogene"

julia> getgeotime(39)
5-element Vector{Pair{String, String}}:
    "Eon" => "Phanerozoic"
    "Era" => "Cenozoic"
 "Period" => "Paleogene"
  "Epoch" => "Eocene"
    "Age" => "Bartonian"

julia> getgeotime(3900, 3) == nothing
true

julia> getgeotime(3900)
2-element Vector{Pair{String, String}}:
 "Eon" => "Archean"
 "Era" => "Eoarchean"
```
