```
akima(x, y, xpt, delta=0.0, eps=1e-30)
```

A convenience method to perform construction and evaluation of the spline in one step. See docstring for Akima for more details.

**Arguments**

  * `x, y::Vector{Float}`: the node points
  * `xpt::Vector{Float} or ::Float`: the evaluation point(s)
  * `delta_x::Float=0.0` : the half width of a smoothing interval used for the absolute

value function.

  * `eps::Float=1e-30` : a cutoff used to avoid dividing by zero in the

weighting function. Default is `1e-30` but this could be raised to machine precision in some cases to improve derivatives.

**Returns**

  * `ypt::Vector{Float} or ::Float`: interpolated value(s) at xpt using akima spline.
