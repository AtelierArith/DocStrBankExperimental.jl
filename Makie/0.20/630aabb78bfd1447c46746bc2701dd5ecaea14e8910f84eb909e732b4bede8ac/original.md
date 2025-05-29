```
datashader(points::AbstractVector{<: Point})
```

!!! warning
    This feature might change outside breaking releases, since the API is not yet finalized. Please be vary of bugs in the implementation and open issues if you encounter odd behaviour.


Points can be any array type supporting iteration & getindex, including memory mapped arrays. If you have separate arrays for x and y coordinates and want to avoid conversion and copy, consider using:

```Julia
using Makie.StructArrays
points = StructArray{Point2f}((x, y))
datashader(points)
```

Do pay attention though, that if x and y don't have a fast iteration/getindex implemented, this might be slower then just copying it into a new array.

For best performance, use `method=Makie.AggThreads()` and make sure to start julia with `julia -tauto` or have the environment variable `JULIA_NUM_THREADS` set to the number of cores you have.

## Attributes

### Specific to `DataShader`

  * `agg = AggCount()` can be `AggCount()`, `AggAny()` or `AggMean()`. User extendable by overloading:

````
```Julia
    struct MyAgg{T} <: Makie.AggOp end
    MyAgg() = MyAgg{Float64}()
    Makie.Aggregation.null(::MyAgg{T}) where {T} = zero(T)
    Makie.Aggregation.embed(::MyAgg{T}, x) where {T} = convert(T, x)
    Makie.Aggregation.merge(::MyAgg{T}, x::T, y::T) where {T} = x + y
    Makie.Aggregation.value(::MyAgg{T}, x::T) where {T} = x
```
````

  * `method = AggThreads()` can be `AggThreads()` or `AggSerial()`.
  * `async::Bool = true` will calculate get_aggregation in a task, and skip any zoom/pan updates while busy. Great for interaction, but must be disabled for saving to e.g. png or when inlining in documenter.
  * `operation::Function = automatic` Defaults to `Makie.equalize_histogram` function which gets called on the whole get*aggregation array before display (`operation(final*aggregation_result)`).
  * `local_operation::Function = identity` function which gets call on each element after the aggregation (`map!(x-> local_operation(x), final_aggregation_result)`).
  * `point_transform::Function = identity` function which gets applied to every point before aggregating it.
  * `binsize::Number = 1` factor defining how many bins one wants per screen pixel. Set to n > 1 if you want a corser image.
  * `show_timings::Bool = false` show how long it takes to aggregate each frame.
  * `interpolate::Bool = true` If the resulting image should be displayed interpolated.

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
