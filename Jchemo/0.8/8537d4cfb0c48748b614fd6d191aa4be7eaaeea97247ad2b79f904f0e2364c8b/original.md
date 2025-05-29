```
thresh_soft(x::Real, delta)
```

Soft thresholding function.

  * `x` : Value to transform.
  * `delta` : Range for the thresholding.

The returned value is:

  * sign(`x`) * max(0, abs(`x`) - `delta`)

where delta >= 0.

## Examples

```julia
using Jchemo, CairoMakie 

delta = .7
thresh_soft(3, delta)

x = LinRange(-2, 2, 100)
y = thresh_soft.(x, delta)
lines(x, y; axis = (xlabel = "x", ylabel = "f(x)"))
```
