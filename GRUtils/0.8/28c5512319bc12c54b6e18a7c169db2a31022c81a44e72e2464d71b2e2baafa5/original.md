```
colorscheme!(p, scheme)
```

Apply a color `scheme` to the given plot `p`, which can be a `PlotObject`, or a `Figure` (in such case the scheme is applied to all the plots contained in it).

The value of `scheme` can be the number or the name of any available color scheme (see [`colorscheme`](@ref) for more details).

Use the keyword argument `scheme` in plotting functions, to set a particular color scheme during the creation of plots (in this case only the number of an already exisiting scheme is allowed).

# Examples

```julia
# Create a plot with a dark scheme (2)
plot(x, y, scheme=2)
# Change it to the standard light scheme
colorscheme!(currentplot(), "light")
```
