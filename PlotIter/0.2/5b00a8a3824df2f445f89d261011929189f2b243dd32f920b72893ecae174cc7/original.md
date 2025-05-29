```
plot_iter(f::Function, iterable; kwargs...)
```

Generate one plot per item of `iterable`.

This function will call `f` for each item in `iterable`, with a new plot set as `Plots.current()`.

It is optimised for use within a Jupyter notebook. It will let you quickly generate a number of plots, making use of the available page width. The plots are then close together, so easier to compare visually.

This function avoids the need to manually construct a layout for this simple case.

# Arguments

  * `f::Function`: A function that takes a single argument of type `eltype(iterable)`. Any   return value is ignored.
  * `iterable`: Any iterable object.

# Keyword arguments

  * `num_cols::Integer=3`: The number of of plots to put side-by-side.
  * `row_width=900`: The width of each row (that is for *all* plots in the row)
  * `row_height=300`: The vertical extent of each plot.
  * `display_mode::DisplayMode=DisplayAtEnd()`: An instance of:

      * [`NoDisplay`](@ref): Don't `show` the plots.
      * [`DisplayEachRow`](@ref): Every time a row of plots is complete, `show` it.
      * [`DisplayAtEnd`](@ref): Wait until all plots are generated, and then show all at once.
  * `xlims_convex_hull::Bool=false`: Iff true, call [`xlims_convex_hull!`](@ref) on all plots.   This requires the `display_mode` to be [`NoDisplay`](@ref) or [`DisplayAtEnd`](@ref).
  * `ylims_convex_hull::Bool=false`: Iff true, call [`ylims_convex_hull!`](@ref) on all plots.   This requires the `display_mode` to be [`NoDisplay`](@ref) or [`DisplayAtEnd`](@ref).
  * `zlims_convex_hull::Bool=false`: Iff true, call [`zlims_convex_hull!`](@ref) on all plots.   This requires the `display_mode` to be [`NoDisplay`](@ref) or [`DisplayAtEnd`](@ref).
  * `clims_convex_hull::Bool=false`: Iff true, call [`clims_convex_hull!`](@ref) on all plots.   This requires the `display_mode` to be [`NoDisplay`](@ref) or [`DisplayAtEnd`](@ref).
  * `kwargs...`: Any other keyword arguments specified will be forwarded to an initial call to   `plot`.

# Returns

A vector of all plots that have been generated.

# Example

Here is the simplest use, with no configuration:

```julia
plot_iter(1:3) do i
    # Note: call to `plot!` rather than `plot` is important, since a new plot object has
    # already been created by `plot_iter`.
    plot!(i .* rand(30))
end;
```

We can also change the sizes, as well as make the y-axis limits match:

```julia
plot_iter(1:3; num_cols=2, row_height=500, ylims_convex_hull=true) do i
    plot!(i .* rand(30))
end;
```
