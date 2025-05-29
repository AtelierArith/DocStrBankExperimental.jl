```
B = padarray(A, padsize; padval=nothing)
```

Pad matrix A with an amount of padding in each dimension specified by padsize.

### Args

  * `A`: GMTimage, GMTgrid or Matrix to pad.
  * `padsize`: Amount of padding in each dimension. It can be a scalar or a array of length equal to 2 or 4 (only matrices are supported).

### Kwargs

  * `padval`: If not specified, `A` is padded with a replication of the first/last row and column, otherwise `padval` specifies a constant value to use for padded elements. `padval` can take the value -Inf or Inf, in which case the smallest or largest representable value of the type of `A` is used, respectively.

### Return

Padded array of same type as input.

### Examples

```julia
julia> padarray(ones(Int,2,3), (1,2); padval=0)
4×7 Matrix{Int64}:
 0  0  0  0  0  0  0
 0  0  1  1  1  0  0
 0  0  1  1  1  0  0
 0  0  0  0  0  0  0
```

Padd with a different number of rows and columns on left-right and top-botom

```julia
 julia> padarray(ones(Int,2,3), (1,2,2,1); padval=0)
5×6 Matrix{Int64}:
 0  0  0  0  0  0
 0  0  1  1  1  0
 0  0  1  1  1  0
 0  0  0  0  0  0
 0  0  0  0  0  0
```
