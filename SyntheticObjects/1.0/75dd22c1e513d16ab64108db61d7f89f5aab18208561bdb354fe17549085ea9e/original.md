```
draw_sphere!(arr, radius, center; thickness=0.8, intensity=one(eltype(arr)))
```

Draw a sphere in a 3D array by adding a Gaussian profile to the array.

#Arguments:

  * `arr::Array`: A 3D array to which the sphere will be added.
  * `radius`: The radius of the sphere as a number or tuple.
  * `center`: The center of the sphere as a tuple. DEFAULT: size(arr).÷2 .+1 which is the (bottom-right) pixel from the center of the array
  * `thickness`: The thickness of the sphere. Default is 0.8.
  * `intensity::Float64`: The intensity of the sphere. Default is 1.0.

# Example

```jldoctest
julia> arr = zeros(Float32, (128, 128, 128));
julia> draw_sphere!(arr, 10);

julia> draw_sphere!(arr, (20,30,40), (50,30,80));
```
