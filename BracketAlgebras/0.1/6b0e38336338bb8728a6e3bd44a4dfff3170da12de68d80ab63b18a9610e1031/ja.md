```
BracketAlgebra(n::Integer, d::Integer, point_ordering::AbstractVector{<:Integer}=collect(1:n), coefficient_ring::AbstractAlgebra.Ring=AbstractAlgebra.ZZ; point_labels::AbstractVector=collect(1:n))


BracketAlgebra(n::Integer, d::Integer, point_ordering::AbstractVector{<:Integer}=collect(1:n), T::Type=Int; point_labels::AbstractVector=collect(1:n))
```

与えられた点の順序と点のラベルを持つ n 点上の射影空間 P^d に対するブラケット代数を構築します。`point*labels` が整数のベクトルである場合、それは `collect(1:n)` と等しいことが期待されます。`coefficient*ring` は、ブラケット代数の係数を含む環です。

# 例

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
