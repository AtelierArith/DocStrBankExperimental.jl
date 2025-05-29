```
gf_pretty(v::Vector{F}, α::F)::Vector{String} where F <: GaloisFields.AbstractGaloisField
```

Pretty print a vector of Galois field elements using `gf_pretty(a, α)` for each element.

# Arguments

  * `v::Vector{F}`: The vector of Galois field elements.
  * `α::F`: The primitive element of the field.

# Returns

  * `Vector{String}`: A vector of string representations.
