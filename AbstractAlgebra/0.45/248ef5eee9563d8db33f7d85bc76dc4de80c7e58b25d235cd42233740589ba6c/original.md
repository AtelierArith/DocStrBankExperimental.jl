```
similarity!(A::MatrixElem{T}, r::Int, d::T) where {T <: RingElement}
```

Applies a similarity transform to the $n\times n$ matrix $M$ in-place. Let $P$ be the $n\times n$ identity matrix that has had all zero entries of row $r$ replaced with $d$, then the transform applied is equivalent to $M = P^{-1}MP$. We require $M$ to be a square matrix. A similarity transform preserves the minimal and characteristic polynomials of a matrix.

# Examples

```jldoctest
julia> R, = residue_ring(ZZ, 7);

julia> S = matrix_space(R, 4, 4)
Matrix space of 4 rows and 4 columns
  over residue ring of integers modulo 7

julia> M = S([R(1) R(2) R(4) R(3); R(2) R(5) R(1) R(0);
              R(6) R(1) R(3) R(2); R(1) R(1) R(3) R(5)])
[1   2   4   3]
[2   5   1   0]
[6   1   3   2]
[1   1   3   5]

julia> similarity!(M, 1, R(3))

```
