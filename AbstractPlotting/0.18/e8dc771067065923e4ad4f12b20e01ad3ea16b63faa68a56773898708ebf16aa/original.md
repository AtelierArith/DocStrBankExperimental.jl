# Plot Recipes in `AbstractPlotting`

There's two types of recipes. *Type recipes* define a simple mapping from a user defined type to an existing plot type. *Full recipes* can customize the theme and define a custom plotting function.

## Type recipes

Type recipe are really simple and just overload the argument conversion pipeline. This can be done for all plot types or for a subset of plot types:

```
# All plot types
convert_arguments(P::Type{<:AbstractPlot}, x::MyType) = convert_arguments(P, rand(10, 10))
# Only for scatter plots
convert_arguments(P::Type{<:Scatter}, x::MyType) = convert_arguments(P, rand(10, 10))
```

Optionally you may define the default plot type so that `plot(x::MyType)` will use this:

```
plottype(::MyType) = Surface
```

## Full recipes with the `@recipe` macro

A full recipe for `MyPlot` comes in two parts. First is the plot type name, arguments and theme definition which are defined using the `@recipe` macro. Second is a custom `plot!` for `MyPlot`, implemented in terms of the atomic plotting functions.

We use an example to show how this works:

```
# arguments (x, y, z) && theme are optional
@recipe(MyPlot, x, y, z) do scene
    Attributes(
        plot_color => :red
    )
end
```

This macro expands to several things. Firstly a type definition:

```
const MyPlot{ArgTypes} = Combined{myplot, ArgTypes}
```

The type parameter of `Combined` contains the function instead of e.g. a symbol. This way the mapping from `MyPlot` to `myplot` is safer and simpler. (The downside is we always need a function `myplot` - TODO: is this a problem?)

The following signatures are defined to make `MyPlot` nice to use:

```
myplot(args...; kw_args...) = ...
myplot!(scene, args...; kw_args...) = ...
myplot(kw_args::Dict, args...) = ...
myplot!(scene, kw_args::Dict, args...) = ...
#etc (not 100% settled what signatures there will be)
```

A specialization of `argument_names` is emitted if you have an argument list `(x,y,z)` provided to the recipe macro:

```
argument_names(::Type{<: MyPlot}) = (:x, :y, :z)
```

This is optional but it will allow the use of `plot_object[:x]` to fetch the first argument from the call `plot_object = myplot(rand(10), rand(10), rand(10))`, for example. Alternatively you can always fetch the `i`th argument using `plot_object[i]`, and if you leave out the `(x,y,z)`, the default version of `argument_names` will provide `plot_object[:arg1]` etc.

The theme given in the body of the `@recipe` invocation is inserted into a specialization of `default_theme` which inserts the theme into any scene that plots `MyPlot`:

```
function default_theme(scene, ::MyPlot)
    Attributes(
        plot_color => :red
    )
end
```

As the second part of defining `MyPlot`, you should implement the actual plotting of the `MyPlot` object by specializing `plot!`:

```
function plot!(plot::MyPlot)
    # normal plotting code, building on any previously defined recipes
    # or atomic plotting operations, and adding to the combined `plot`:
    lines!(plot, rand(10), color = plot[:plot_color])
    plot!(plot, plot[:x], plot[:y])
    plot
end
```

It's possible to add specializations here, depending on the argument *types* supplied to `myplot`. For example, to specialize the behavior of `myplot(a)` when `a` is a 3D array of floating point numbers:

```
const MyVolume = MyPlot{Tuple{<:AbstractArray{<: AbstractFloat, 3}}}
argument_names(::Type{<: MyVolume}) = (:volume,) # again, optional
function plot!(plot::MyVolume)
    # plot a volume with a colormap going from fully transparent to plot_color
    volume!(plot, plot[:volume], colormap = :transparent => plot[:plot_color])
    plot
end
```

The docstring given to the recipe will be transferred to the functions it generates.
