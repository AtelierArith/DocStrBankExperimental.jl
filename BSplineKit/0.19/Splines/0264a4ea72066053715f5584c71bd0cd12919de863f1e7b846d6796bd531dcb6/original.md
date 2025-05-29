```
integral(S::Spline)
```

Returns an antiderivative of the given spline as a new spline.

The algorithm is described in de Boor 2001, p. 127.

Note that the integral spline `I` returned by this function is defined up to a constant. By convention, here the returned spline `I` is zero at the left boundary of the domain. One usually cares about the integral of `S` from point `a` to point `b`, which can be obtained as `I(b) - I(a)`.

!!! note "Periodic splines"
    Note that the integral of a periodic function is in general not periodic. For periodic splines (backed by a [`PeriodicBSplineBasis`](@ref)), this function returns a non-periodic spline (backed by a regular [`BSplineBasis`](@ref)).

