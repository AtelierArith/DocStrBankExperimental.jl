```
CanonicalSymplecticMatrix{T}(n::Integer)
```

constructs a canonical symplectic matrix of size `(n, n)` with eltype `T`. `n` must be even and positive. See the examples to see the form of the canonical symplectic matrix as defined here.

# Examples

```jldoctest
julia> CanonicalSymplecticMatrix(4)
4×4 CanonicalSymplecticMatrix{Int64}:
 0  0  -1   0
 0  0   0  -1
 1  0   0   0
 0  1   0   0

julia> CanonicalSymplecticMatrix{Int32}(6)
6×6 CanonicalSymplecticMatrix{Int32}:
 0  0  0  -1   0   0
 0  0  0   0  -1   0
 0  0  0   0   0  -1
 1  0  0   0   0   0
 0  1  0   0   0   0
 0  0  1   0   0   0
```
