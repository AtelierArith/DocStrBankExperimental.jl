```
cube_label(pointdim::Int, pointlen::Int, pointinfo::Vector{Int})
```

Create a label from a cube's coordinate information.

The dimension of the ambient Eucliden space is `pointdim`, while the field length for each coordinate is `pointlen`. The vector `pointinfo` has to be of length at least two times `pointdim`. The first `pointdim` entries contain the coordinates of the anchor point, while the next `pointdim` entries are either 0 or 1 depending on the size of the interval. For example, if `poindim = 3` and `pointinfo = [1,2,3,1,0,1]`, then we represent the cube in three-dimensional space given by `[1,2] x [2] x [3 4]`.

# Example

```jldoctest
julia> cube_label(3,2,[10,23,5,1,1,0])
"102305.110"
```
