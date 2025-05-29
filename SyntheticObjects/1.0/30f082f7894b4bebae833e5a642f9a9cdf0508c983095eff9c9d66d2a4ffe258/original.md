hollow_sphere([DataType], sz= (128, 128, 128), radius=0.8, center=sz.÷2 .+1; thickness=0.8)

Create a 3D representation of a hollow sphere.

# Arguments

  * `DataType`: The optional datatype of the output array. Default is Float32.
  * `sz`: A vector of integers representing the size of the sphere.
  * `radius`: A float representing the radius of the sphere.
  * `thickness`: A float representing the thickness of the sphere in pixels. Default is 0.8.
  * `center`: A tuple representing the center of the sphere. Default is the center of the object.

# Returns

  * `sph::Array{Float64}`: A 3D array representing the hollow sphere.

# Example

```jldoctest
# create a centered sphere of 80% of the object size with a thickness of 0.8 pixels
julia> hollow_sphere()
```
