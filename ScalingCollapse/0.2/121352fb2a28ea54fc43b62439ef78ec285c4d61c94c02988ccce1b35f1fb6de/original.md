```
ScalingFunction(preset::Symbol; kwargs...)
ScalingFunction(f::Function; kwargs...)
```

A `ScalingFunction` is used in a `ScalingProblem` to rescale the data. It is defined by a function `f` and a set of parameters `p_names`. The function `f` is called with the data `d` and the parameters `p1`, `p2`, ... and returns a new `Data` object.

# Arguments

  * `preset::Symbol`: a preset for the `ScalingFunction`. See `Presets` below.
  * `f::Function`: the function `f` to be used in the `ScalingFunction`. Pass this   argument to create a custom `ScalingFunction`. f should take a `Data` object   and a set of parameters `p1`, `p2`, ... and return a new `Data` object:   f(d::Data, p1, p2, ...) -> Data.

    Note that you might want to set the function `f` as a keyword argument to   use the "fixing parameters" feature (see below).

# Presets

The `preset` argument can be used to create a `ScalingFunction` with a preset function `f` and a preset set of parameter names `p_names`. The following presets are available:

  * `:x` rescale the x values of the data according to x -> (x - p1)/p1 * L^(1/p2)
  * `:xy` rescale the x and y values of the data according to x -> (x - p1)/p1 * L^(1/p2)   and y -> y * L^(p3/p2)
  * `:xny` rescale the x and y values of the data according to x -> (x - p1)/p1 * L^(1/p2)   and y -> y * L^(-p3/p2)

# Keyword arguments

  * `p_names::Vector{String}`: the parameter names `p_names` to be used in the   `ScalingFunction`. This kwarg can be used to overwrite the preset parameter   names `p_names` (p1, p2, ...).
  * `f::Function`: the function `f` to be used in the `ScalingFunction`. This kwarg can   be used to overwrite the preset function `f`. If you pass f as a kwarg, instead of   an argument, you can use the "fixing parameters" feature (see below). In that case   the number of paramters of your function f should match the preset, i.e. if your   function f takes 2 parameters, you should use the preset `:x` and if your function   f takes 3 parameters, you should use the preset `:xy`.
  * `x_scale::String`: the scaling function for the x values. This is just used to   display the scaling function in plots and julias show function.
  * `y_scale::String`: the scaling function for the y values. This is just used to   display the scaling function in plots and julias show function.
  * `p::Float64`: fix a parameter to a value. If you know the analytical value of a scaling   parameter you might want to fix it to this value. This can speed up the optimization   and give better results. Note, that `p` is either "p1", "p2", ... or the name you   specified in `p_names`.

    Note that this feature is only available if you use one of the presets. You can still   modify the scaling function by setting `f` as a kwarg.

# Examples

### Presets

```julia
# rescale the x axis only
ScalingFunction(:x; p_names=["T_c", "nu"])

# lets fix nu to 1.0
ScalingFunction(:x; p_names=["T_c", "nu"], nu=1.0)

# rescale the x and y axis
ScalingFunction(:xy; p_names=["T_c", "nu", "beta"])

# rescale the x and y axis with negative exponent on y
ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"])
```

### Custom scaling function

```julia
# define the function that scales the data
function myfunction(d::ScalingCollapse.Data, p1, p2)

    #  initialize arrays for scaled data
    xs = zeros(length(d.xs))
    ys = zeros(length(d.ys))
    es = zeros(length(d.es))

    # scale data according to p1 and p2
    for (i, x, y, e) in zip(eachindex(d.xs), d.xs, d.ys, d.es)
        xs[i] = (x - p1) / p1 * log(d.L)
        ys[i] = y * d.L^(p2)
        es[i] = e * d.L^(p2)
    end

    # create new Data object with scaled data
    return ScalingCollapse.Data(d.L, xs, ys, es)
end

ScalingFunction(myfunction; p_names=["myp1", "myp2"])

# lets say we want to fix the parameter "myp1" to 1.0
# we use the preset :x (because it also has 2 parameters) and overwrite the function f
ScalingFunction(:x; f=myfunction, p_names=["myp1", "myp2"], myp1=1.0)
```
