```julia
lowess(x, y, span = 2 / 3, nsteps = 3, delta = 0.01 * (maximum(x) - minimum(x)))
```

Compute the smooth of a scatterplot of `y` against `x` using robust locally weighted regression. Input vectors `x` and `y` must contain either integers or floats. Parameters `span` and `delta` must be of type `T`, where `T <: AbstractFloat`. Returns a vector `ys`; `ys[i]` is the fitted value at `x[i]`. To get the smooth plot, `ys` must be plotted against `x`.

# Arguments

  * `x::Vector`: Abscissas of the points on the scatterplot. `x` must be ordered.
  * `y::Vector`: Ordinates of the points in the scatterplot.
  * `span`: The amount of smoothing.
  * `nsteps::Integer`: Number of iterations in the robust fit.
  * `delta`: A nonnegative parameter which may be used to save computations. Default is `0.01 * (maximum(x) - minimum(x))`.

# Example

```julia
x = sort(10 .* rand(100))
y = sin.(x) .+ 0.5 * rand(100)
ys = lowess(x, y, span=0.2)
scatter(x, y)
plot!(x, ys)
```
