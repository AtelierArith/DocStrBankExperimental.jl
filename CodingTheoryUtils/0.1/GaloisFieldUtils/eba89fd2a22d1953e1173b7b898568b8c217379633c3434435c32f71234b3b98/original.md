```
one_hot_vector(len::Int, pos::Int, v::F) where F <: AbstractGaloisField -> Vector{F}
```

Create a one-hot vector of length `len` with value `v` at position `pos`. All other elements will be zero in the field `F`.

# Arguments

  * `len::Int`: The length of the resulting vector.
  * `pos::Int`: The 1-based index where the value `v` should be placed.
  * `v::F`: The value to place at the specified position.

# Returns

  * `Vector{F}`: The resulting one-hot vector.

# Examples

julia> one*hot*vector(5, 3, F2(1)) 5-element Vector{F2}:  0  0  1  0  0

julia> GF8, α = GaloisField(2, 3, :α);

julia> one*hot*vector(4, 2, α^3) 4-element Vector{GF8}:  0  α^3  0  0
