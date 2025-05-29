```
Vandermonde(c::AbstractVector)
```

Create a "lazy" `n × n` [`Vandermonde` matrix](https://en.wikipedia.org/wiki/Vandermonde_matrix) where $A_{ij} = c_i^{j-1}$, requiring only `O(n)` storage for the vector `c`.

The `transpose` and `adjoint` operations are also lazy.

```jldoctest van
julia> a = 1:5; A = Vandermonde(a)
5×5 Vandermonde{Int64}:
 1  1   1    1    1
 1  2   4    8   16
 1  3   9   27   81
 1  4  16   64  256
 1  5  25  125  625

julia> A'
5×5 adjoint(::Vandermonde{Int64}) with eltype Int64:
 1   1   1    1    1
 1   2   3    4    5
 1   4   9   16   25
 1   8  27   64  125
 1  16  81  256  625
```

The backslash operator `\` is overloaded to solve Vandermonde and adjoint Vandermonde systems in `O(n^2)` time using the algorithm of Björck & Pereyra (1970), https://doi.org/10.2307/2004623.

```jldoctest van
julia> A \ a
5-element Vector{Float64}:
 0.0
 1.0
 0.0
 0.0
 0.0

julia> A' \ A[2,:]
5-element Vector{Float64}:
 0.0
 1.0
 0.0
 0.0
 0.0
```
