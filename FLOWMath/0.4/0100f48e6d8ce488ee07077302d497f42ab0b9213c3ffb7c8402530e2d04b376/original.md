```
gradient(spline, x)
```

Computes the gradient of a Akima spline at x.

**Arguments**

  * `spline::Akima}`: an Akima spline
  * `x::Vector{Float}`: the evaluation point(s)

**Returns**

  * `dydx::Vector{Float}`: gradient at x using akima spline.
