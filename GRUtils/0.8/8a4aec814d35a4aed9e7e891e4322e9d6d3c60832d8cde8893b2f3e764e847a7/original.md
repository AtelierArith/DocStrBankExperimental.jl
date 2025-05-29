```
volume(v; kwargs...)
```

Draw a the three-dimensional array `v`, using volume rendering.

The volume data is reduced to a two-dimensional image using an emission or absorption model, or by a maximum intensity projection. After the projection the current colormap is applied to the result.

The method to reduce volume data can be defined by the keyword argument `algorithm` –- a number or a string from the following table:

|  #  | String         | description                  |
|:---:|:-------------- |:---------------------------- |
|  0  | `"emission"`   | emission model (default)     |
|  1  | `"absorption"` | absorption model             |
|  2  | `"mip"`        | maximum intensity projection |

# Examples

```julia
# Create example data
x = LinRange(-1, 1, 40)
y = LinRange(-1, 1, 40)
z = LinRange(-1, 1, 40)
v = 1 .- (x.^2 .+ y'.^2 .+ reshape(z,1,1,:).^2).^0.5 - 0.25 .* rand(40, 40, 40)
# Draw the 3d volume data using an emission model
volume(v, algorithm="mip")

```
