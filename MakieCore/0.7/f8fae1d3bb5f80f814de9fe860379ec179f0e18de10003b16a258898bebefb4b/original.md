```
meshscatter(positions)
meshscatter(x, y)
meshscatter(x, y, z)
```

Plots a mesh for each element in `(x, y, z)`, `(x, y)`, or `positions` (similar to `scatter`). `markersize` is a scaling applied to the primitive passed as `marker`.

## Attributes

### Specific to `MeshScatter`

  * `color = theme(scene, :markercolor)` sets the color of the marker. If no color is set, multiple calls to `meshscatter!` will cycle through the axis color palette. Otherwise, one can set one color per point by passing a `Vector{<:Colorant}`, or one colorant for the whole meshscatterplot. If color is a vector of numbers, the colormap args are used to map the numbers to colors.
  * `cycle::Vector{Symbol} = [:color]` sets which attributes to cycle when creating multiple plots.
  * `marker::Union{Symbol, GeometryBasics.GeometryPrimitive, GeometryBasics.Mesh}` sets the scattered mesh.
  * `markersize::Union{<:Real, Vec3f} = 0.1` sets the scale of the mesh. This can be given as a Vector to apply to each scattered mesh individually.
  * `rotations::Union{Real, Vec3f, Quaternion} = 0` sets the rotation of the mesh. A numeric rotation is around the z-axis, a `Vec3f` causes the mesh to rotate such that the the z-axis is now that vector, and a quaternion describes a general rotation. This can be given as a Vector to apply to each scattered mesh individually.

### 3D shading attributes

  * `shading = Makie.automatic` sets the lighting algorithm used. Options are `NoShading` (no lighting), `FastShading` (AmbientLight + PointLight) or `MultiLightShading` (Multiple lights, GLMakie only). Note that this does not affect RPRMakie.
  * `diffuse::Vec3f = Vec3f(1.0)` sets how strongly the red, green and blue channel react to diffuse (scattered) light.
  * `specular::Vec3f = Vec3f(0.4)` sets how strongly the object reflects light in the red, green and blue channels.
  * `shininess::Real = 32.0` sets how sharp the reflection is.
  * `backlight::Float32 = 0f0` sets a weight for secondary light calculation with inverted normals.
  * `ssao::Bool = false` adjusts whether the plot is rendered with ssao (screen space ambient occlusion). Note that this only makes sense in 3D plots and is only applicable with `fxaa = true`.

### Color attributes

  * `colormap::Union{Symbol, Vector{<:Colorant}} = :viridis` sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.
  * `colorscale::Function = identity` color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.
  * `colorrange::Tuple{<:Real, <:Real}` sets the values representing the start and end points of `colormap`.
  * `nan_color::Union{Symbol, <:Colorant} = RGBAf(0,0,0,0)` sets a replacement color for `color = NaN`.
  * `lowclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value below the colorrange.
  * `highclip::Union{Nothing, Symbol, <:Colorant} = nothing` sets a color for any value above the colorrange.
  * `alpha = 1.0` sets the alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.

### Generic attributes

  * `visible::Bool = true` sets whether the plot will be rendered or not.
  * `overdraw::Bool = false` sets whether the plot will draw over other plots. This specifically means ignoring depth checks in GL backends.
  * `transparency::Bool = false` adjusts how the plot deals with transparency. In GLMakie `transparency = true` results in using Order Independent Transparency.
  * `fxaa::Bool = true` adjusts whether the plot is rendered with fxaa (anti-aliasing).
  * `inspectable::Bool = true` sets whether this plot should be seen by `DataInspector`.
  * `depth_shift::Float32 = 0f0` adjusts the depth value of a plot after all other transformations, i.e. in clip space, where `0 <= depth <= 1`. This only applies to GLMakie and WGLMakie and can be used to adjust render order (like a tunable overdraw).
  * `model::Makie.Mat4f` sets a model matrix for the plot. This replaces adjustments made with `translate!`, `rotate!` and `scale!`.
  * `space::Symbol = :data` sets the transformation space for box encompassing the volume plot. See `Makie.spaces()` for possible inputs.
