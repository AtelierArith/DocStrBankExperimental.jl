```
simplex_volume(distances::CayleyMengerDistanceMatrix{T,Sz}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {N,T<:Real}
simplex_volume(points::Vararg{NTuple{N,T},N+1}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {N,T<:Real}
simplex_volume(P::AbstractMatrix{T}; distance_type::Union{Nothing,Type{<:Real}} = nothing) where {T<:Real}
```

Calculates the (interior) measure of an `N`-simplex given the coordinates of its points, using the Cayley-Menger determinant involving the squared distances between the points.

For example, if `N == 2`, then this function calculates the area of a triangle given the 2-dimensional coordinates of its 3 points; likewise, if `N == 3`, then then this function calculates the volume of a tetrahedron given the 3-dimensional coordinates of its 4 points.

When providing `points`, it must be N+1 tuples of N values each, which are the coordinates of the points of the `N`-simplex. When providing `P`, it must be a tall near-square matrix with N+1 rows and N columns, where the rows are the coordinates of the points of the `N`-simplex.

If `distance_type` is provided and is not `nothing`, then the internal calculations on the squared distances will be done using `distance_type` as the type; otherwise, the type used for the internal calculations will be automatically derived from `T`.
