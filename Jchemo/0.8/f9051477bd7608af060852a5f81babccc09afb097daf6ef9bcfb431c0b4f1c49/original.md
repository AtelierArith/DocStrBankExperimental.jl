```
thresh_hard(x::Real, delta)
```

Hard thresholding function.

  * `x` : Value to transform.
  * `delta` : Range for the thresholding.

The returned value is:

  * abs(`x`) > `delta` ? `x` : 0

where delta >= 0.

## Examples

```julia
using Jchemo, CairoMakie 

delta = .7
thresh_hard(3, delta)

x = LinRange(-2, 2, 500)
y = thresh_hard.(x, delta)
lines(x, y; axis = (xlabel = "x", ylabel = "f(x)"))
```
