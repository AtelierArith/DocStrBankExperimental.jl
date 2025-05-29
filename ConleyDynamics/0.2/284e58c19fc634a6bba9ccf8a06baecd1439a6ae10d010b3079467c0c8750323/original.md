```
cube_information(cube::String)
```

Compute a cube's coordinate information.

The function returns an integer vector with the cubes coordinate information. The return vector `intinfo` contains in its components the following data:

  * `1:pointdim`: Coordinates of the anchor point
  * `1+pointdim:2*pointdim`: Interval length in each dimension
  * `1+2*pointdim`: Dimension of the cube

Note that `pointdim` equals the dimension of the points specifying the cube.

# Example

```jldoctest
julia> cube_information("011654003.011")
7-element Vector{Int64}:
  11
 654
   3
   0
   1
   1
   2
```
