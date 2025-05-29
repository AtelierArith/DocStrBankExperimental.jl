```
get_interp(A::Matrix, axes; B=<interpolation-type>)
```

Generate a 5D interpolation object for a given τ or Tₑₓ cube where the last dimension indexes the transition number. By default a second order (quadratic) interpolation is used with flat extrapolation for out-of-bounds access. The axis containing the transition number is not interpolated – an exactly matching value must be given.

Please ensure that the axes passed have a linear step size (nb. use log(n) or log(N) axes if using logarithmically spaced values). A gridded interpolation object can be created using the `Gridded` interpolation type.
