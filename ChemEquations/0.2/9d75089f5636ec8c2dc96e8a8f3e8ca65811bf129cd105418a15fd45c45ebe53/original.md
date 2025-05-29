```julia
elements(compound::ChemEquations.Compound) -> Vector{String}

```

Returns compound's elements as strings.

# Examples

```jldoctest
julia> elements(cc"CH3COOH")
3-element Array{String,1}:
 "C"
 "H"
 "O"
```
