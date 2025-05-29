```
BracketAlgebra(n::Integer, d::Integer, point_ordering::AbstractVector{<:Integer}=collect(1:n), coefficient_ring::AbstractAlgebra.Ring=AbstractAlgebra.ZZ; point_labels::AbstractVector=collect(1:n))


BracketAlgebra(n::Integer, d::Integer, point_ordering::AbstractVector{<:Integer}=collect(1:n), T::Type=Int; point_labels::AbstractVector=collect(1:n))
```

Construct a bracket algebra over the projective space P^d on n points with the given point ordering and point labels. If point*labels is a vector of integers, it is expected to be equal to `collect(1:n)`. `coefficient*ring` is the ring, which contains the coefficients of the bracket algebra.

# Examples

```jldoctest
julia> B = BracketAlgebra(4, 2, [1,2,3,4], point_labels = ["a","b","c","d"])
Bracket algebra over P^2 on 4 points with point ordering a < b < c < d and coefficient ring Integers.
```

```jldoctest
julia> B = BracketAlgebra(4, 2, [2,1,3,4], point_labels = ["a","b","c","d"])
Bracket algebra over P^2 on 4 points with point ordering b < a < c < d and coefficient ring Integers.
```

```jldoctest
julia> B = BracketAlgebra(4, 2, [2,1,3,4], AbstractAlgebra.GF(13), point_labels = ["a","b","c","d"])
Bracket algebra over P^2 on 4 points with point ordering b < a < c < d and coefficient ring Finite field F_13.
```
