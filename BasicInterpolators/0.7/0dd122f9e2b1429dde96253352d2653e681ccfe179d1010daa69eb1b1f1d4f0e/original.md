```
RBFInterpolator(X, y, ϵ, rbf=invmultiquadratic)
```

Construct a radial basis function (RBF) interpolator for an n-dimensional set of points with coordinates `X` and values `y`. `X` must be an p × N array, where p is the number of points and N is the number of dimensions. `y` must be a length p vector. The value of `ϵ` scales the radial basis function of choice, `f`, which is [`invmultiquadratic`](@ref) by default. Any function in the form $ϕ(r,ϵ)$ can be passed to the `rbf` argument, where $r$ is the distance between points and $ϵ$ is a scaling factor.
