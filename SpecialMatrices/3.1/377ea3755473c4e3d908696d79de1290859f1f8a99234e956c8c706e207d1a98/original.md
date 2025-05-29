```
[`Frobenius` matrix](https://en.wikipedia.org/wiki/Frobenius_matrix)
```

Frobenius matrices or Gaussian elimination matrices of the form

```
[ 1 0 ...     0 ]
[ 0 1 ...     0 ]
[ .........     ]
[ ... 1 ...     ]
[ ... c1 1 ...  ]
[ ... c2 0 1 ...]
[ ............. ]
[ ... ck ...   1]
```

i.e., an identity matrix with possibly nonzero subdiagonal elements along a single column.

In this implementation, the subdiagonal of the nonzero column is stored as a dense vector, so that the size can be inferred automatically as j+k, where j is the column index and k is the number of subdiagonal elements.

```jldoctest
julia> using SpecialMatrices

julia> F = Frobenius(3, 4:6) # Specify subdiagonals of column 3
6×6 Frobenius{Int64}:
 1  0  0  0  0  0
 0  1  0  0  0  0
 0  0  1  0  0  0
 0  0  4  1  0  0
 0  0  5  0  1  0
 0  0  6  0  0  1

julia> inv(F) # Special form of inverse
6×6 Frobenius{Int64}:
 1  0   0  0  0  0
 0  1   0  0  0  0
 0  0   1  0  0  0
 0  0  -4  1  0  0
 0  0  -5  0  1  0
 0  0  -6  0  0  1

julia> F*F # Special form preserved if the same column has the subdiagonals
6×6 Frobenius{Int64}:
 1  0   0  0  0  0
 0  1   0  0  0  0
 0  0   1  0  0  0
 0  0   8  1  0  0
 0  0  10  0  1  0
 0  0  12  0  0  1

julia> F*Frobenius(2, 2:5) # Promotes to Matrix
6×6 Matrix{Int64}:
 1   0  0  0  0  0
 0   1  0  0  0  0
 0   2  1  0  0  0
 0  11  4  1  0  0
 0  14  5  0  1  0
 0  17  6  0  0  1

julia> F * [10.0,20,30,40,50,60.0]
6-element Vector{Float64}:
  10.0
  20.0
  30.0
 160.0
 200.0
 240.0
```
