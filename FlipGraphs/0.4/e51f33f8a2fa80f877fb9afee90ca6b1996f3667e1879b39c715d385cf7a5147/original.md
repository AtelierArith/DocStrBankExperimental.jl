```
deltacomplex(s :: Vector{<:Integer})
```

Create a triangulation of an orientable surface with a single point, by gluing the corresponding edges together.

`s` should be an array of nonzero integers representing the edges of a polygon in anticlockwise order.
The i-th edge is orientated anticlockwise if `s[i]>0` and anticlockwise if `s[i]<0`.
If `s[i]` and `s[j]` have the same absolute value, they are glued together while respecting their orientation.

# Examples

The following results in the triangulation of a *torus* with one point:

```julia-rep
julia> deltacomplex([1,2,-1,-2])
```

The following results in the triangulation of a *klein bottle* with one point:

```julia-rep
julia> deltacomplex([1,2,-1,2])
```
