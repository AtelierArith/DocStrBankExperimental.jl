This handy macro will process a function definition, replace `-->` commands, and then add a new version of `RecipesBase.apply_recipe` for dispatching on the arguments.

This functionality is primarily geared to turning user types and settings into the data and attributes that describe a Plots.jl visualization.

Set attributes using the `-->` command, and return a comma separated list of arguments that should replace the current arguments.

An example:

```julia
using RecipesBase

# Our custom type that we want to display
struct T end

@recipe function plot(t::T, n::Integer = 1; customcolor = :green)
    markershape --> :auto, :require
    markercolor --> customcolor, :force
    xrotation --> 5
    zrotation --> 6, :quiet
    rand(10,n)
end

# ---------------------

# Plots will be the ultimate consumer of our recipe in this example
using Plots; gr()

# This call will implicitly call `RecipesBase.apply_recipe` as part of the Plots
# processing pipeline (see the Pipeline section of the Plots documentation).
# It will plot 5 line plots, all with black circles for markers.
# The markershape argument must be supported, and the zrotation argument's warning
# will be suppressed.  The user can override all arguments except markercolor.
plot(T(), 5; customcolor = :black, shape=:c)
```

In this example, we see lots of the machinery in action.  We create a new type `T` which we will use for dispatch, and an optional argument `n`, which will be used to determine the number of series to display.  User-defined keyword arguments are passed through, and the `-->` command can be trailed by flags:

  * quiet:   Suppress unsupported keyword warnings
  * require: Error if keyword is unsupported
  * force:   Don't allow user override for this keyword
