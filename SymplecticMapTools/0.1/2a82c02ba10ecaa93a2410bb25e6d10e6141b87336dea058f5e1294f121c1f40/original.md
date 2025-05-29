```
circle_linear!(z::FourierCircle, FJ::Function, x::AbstractArray, h::Number)
```

Fill `z`'s Fourier coefficients using a linearization about a stable periodic orbit. Useful for seeding continuation.

Arguments:

  * `z`: An invariant circle
  * `FJ`: A function that returns the map and its derivative `F, dFdx = FJ(x)`
  * `x`: A periodic orbit of `F`
  * `h`: The average radius of the first linearized invariant circle
