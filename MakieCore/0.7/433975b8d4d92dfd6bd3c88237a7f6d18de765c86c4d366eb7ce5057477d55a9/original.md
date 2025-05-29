```
volume(volume_data)
volume(x, y, z, volume_data)
```

Plots a volume, with optional physical dimensions `x, y, z`. Available algorithms are:

  * `:iso` => IsoValue
  * `:absorption` => Absorption
  * `:mip` => MaximumIntensityProjection
  * `:absorptionrgba` => AbsorptionRGBA
  * `:additive` => AdditiveRGBA
  * `:indexedabsorption` => IndexedAbsorptionRGBA

## Attributes

### Specific to `Volume`

  * `algorithm::Union{Symbol, RaymarchAlgorithm} = :mip` sets the volume algorithm that is used.
  * `isorange::Real = 0.05` sets the range of values picked up by the IsoValue algorithm.
  * `isovalue = 0.5` sets the target value for the IsoValue algorithm.
  * `interpolate::Bool = true` sets whether the volume data should be sampled with interpolation.

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
