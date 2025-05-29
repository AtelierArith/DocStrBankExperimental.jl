```
CayleyMengerDistanceMatrix{T,Sz}(simplex_dimensions::Int, square_distances::Vector{T}) where {T<:Real,Sz::Union{Int,Dynamic}}
CayleyMengerDistanceMatrix(points::Vararg{NTuple{N,T},N+1})::CayleyMengerDistanceMatrix{T,N} where {T<:Real,N::Int}
CayleyMengerDistanceMatrix(P::AbstractMatrix{T})::CayleyMengerDistanceMatrix{T,Dynamic} where {T<:Real}
```

The zero-diagonal symmetric matrix of square distances among the points of an `N`-simplex, backed by efficient linear storage.

When providing `points`, it must be N+1 tuples of N values each, which are the coordinates of the points of the `N`-simplex. When providing `P`, it must be a tall near-square matrix with N+1 rows and N columns, where the rows are the coordinates of the points of the `N`-simplex. When providing `simplex_dimensions` and `square_distances` directly, `simplex_dimensions` must be the integer number of dimension `N` of the `N-simplex, and`square*distances`must be the precomputed backing linear storage of the square distances among the points of the`N`-simplex and so must have length`binomial2(simplex*dimensions + 1)`.
