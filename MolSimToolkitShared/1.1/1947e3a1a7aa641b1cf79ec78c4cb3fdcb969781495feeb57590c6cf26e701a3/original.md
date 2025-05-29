```
rmsd(x::AbstractVector,y::AbstractVector)
```

Calculate the root mean square deviation between two vectors of coordinates.

# Arguments

  * `x::AbstractVector`: A vector of coordinates.
  * `y::AbstractVector`: A vector of coordinates.

# Returns

  * `rmsd::Real`: The root mean square deviation between the two vectors.

```jldoctest
julia> import MolSimToolkitShared: rmsd

julia> x = [ [1.0, 2.0, 3.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> y = [ [2.0, 3.0, 4.0], [4.0, 5.0, 6.0], [7.0, 8.0, 9.0] ];

julia> rmsd(x, y)
1.0
```
