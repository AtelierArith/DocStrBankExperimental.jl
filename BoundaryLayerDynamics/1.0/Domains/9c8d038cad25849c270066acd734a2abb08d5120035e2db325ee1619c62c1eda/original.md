```
SinusoidalMapping(η, variant = :auto)
```

Define a transformed vertical coordinate with a mapping in the form of

$x_3 = \frac{\sin(ζ η π/2)}{\sin(η π/2)}$

appropriately rescaled such that it maps the range $0≤ζ≤1$ to the $x_3$-range of the [`Domain`](@ref).

The parameter $0<η<1$ controls the strength of the grid stretching, where values close to $0$ result in a more equidistant spacing and values close to $1$ result in a higher density of grid points close to the wall(s). The value $η=1$ is not allowed since it produces a vanishing derivative of the mapping function at the wall.

The `variant` defines at which of the boundaries the coordinates are refined and can be set to `:below`, `:above`, `:symmetric` (both boundaries refined), or `:auto` (refined for boundaries that produce a boundary-layer).
