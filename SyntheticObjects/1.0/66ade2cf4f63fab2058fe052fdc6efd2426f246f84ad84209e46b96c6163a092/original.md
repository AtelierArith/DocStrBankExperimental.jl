hollow_sphere(obj, radius=0.8, center=sz.÷2 .+1; thickness=0.8)

Create a 3D representation of a hollow sphere.

# Arguments

  * `obj`: A 3D array representing the object into which the sphere will be added.
  * `radius`: A float representing the radius of the sphere.
  * `thickness`: A float representing the thickness of the sphere in pixels. Default is 0.8.
  * `center`: A tuple representing the center of the sphere. Default is the center of the object.

# Returns

  * `sph::Array{Float64}`: A 3D array representing the hollow sphere.

# Example

```jldoctest
# create a centered sphere of 80% of the object size with a thickness of 0.8 pixels
julia> obj = zeros(Float64, (128, 128, 128));
julia> hollow_sphere(obj, 0.8)
```
