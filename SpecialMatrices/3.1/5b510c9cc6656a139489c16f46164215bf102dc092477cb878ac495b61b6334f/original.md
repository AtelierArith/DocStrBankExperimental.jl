Hilbert(m [,n])

Construct `m × m` or `m × n` [`Hilbert` matrix](https://en.wikipedia.org/wiki/Hilbert_matrix) from its specified dimensions, where element `i,j` equal to `1 / (i+j-1)`.

```jldoctest hilbert1
julia> A = Hilbert(5)
5×5 Hilbert{Rational{Int64}}:
  1    1//2  1//3  1//4  1//5
 1//2  1//3  1//4  1//5  1//6
 1//3  1//4  1//5  1//6  1//7
 1//4  1//5  1//6  1//7  1//8
 1//5  1//6  1//7  1//8  1//9

julia> Matrix(A)
5×5 Matrix{Rational{Int64}}:
  1    1//2  1//3  1//4  1//5
 1//2  1//3  1//4  1//5  1//6
 1//3  1//4  1//5  1//6  1//7
 1//4  1//5  1//6  1//7  1//8
 1//5  1//6  1//7  1//8  1//9
```

Inverses are also integer matrices:

```jldoctest hilbert1
julia> inv(A)
5×5 InverseHilbert{Rational{Int64}}:
    25    -300     1050    -1400     630
  -300    4800   -18900    26880  -12600
  1050  -18900    79380  -117600   56700
 -1400   26880  -117600   179200  -88200
   630  -12600    56700   -88200   44100
```
