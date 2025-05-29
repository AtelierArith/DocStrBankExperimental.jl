```julia
paley(matrix::Matrix{Int64}) -> Matrix{Int64}

```

The [Paley  construction](https://en.wikipedia.org/wiki/Paley_construction) is a method for constructing Hadamard matrices using finite fields.

```jldoctest
julia> paley(Matrix{Int}(undef, 8, 8))
8×8 Matrix{Int64}:
 -1   1   1  -1   1   1   1  -1
  1   1  -1   1   1   1  -1  -1
  1  -1   1   1   1  -1  -1   1
 -1   1   1   1  -1  -1   1   1
  1   1   1  -1  -1   1   1  -1
  1   1  -1  -1   1   1  -1   1
  1  -1  -1   1   1  -1   1   1
 -1  -1   1   1  -1   1   1   1

```
