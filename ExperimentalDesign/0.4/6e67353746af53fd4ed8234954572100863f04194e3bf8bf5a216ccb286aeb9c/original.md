```julia
plackettburman(matrix_size::Int64) -> Matrix{Int64}

```

Constructs a Plackett-Burman  design with size `matrix_size` if  possible, or to the closest, largest, number for which it is possible.

```jldoctest
julia> plackettburman(4)
8×7 Matrix{Int64}:
  1   1   1   1   1   1   1
 -1   1  -1   1   1  -1  -1
  1  -1   1   1  -1  -1  -1
 -1   1   1  -1  -1  -1   1
  1   1  -1  -1  -1   1  -1
  1  -1  -1  -1   1  -1   1
 -1  -1  -1   1  -1   1   1
 -1  -1   1  -1   1   1  -1

```
