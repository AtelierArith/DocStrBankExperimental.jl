```
from_f2mat_to_intmat(M::Matrix{<:GaloisFields.AbstractGaloisField})::Matrix{Int}
```

Convert a matrix over a Galois field to an integer matrix where 1 is mapped to 1 and 0 is mapped to 0.

# Arguments

  * `M::Matrix{<:GaloisFields.AbstractGaloisField}`: Input matrix over a Galois field

# Returns

  * `Matrix{Int}`: Integer matrix with the same dimensions as the input matrix

# Examples

```julia
julia> F4, α = GaloisField(2, 2, :α)
julia> M = [F4(1) F4(0); F4(0) F4(1)]
julia> from_f2mat_to_intmat(M)
2×2 Matrix{Int64}:
 1  0
 0  1
```
