```
ParametrizedCurve(fun, range = (0.0, 1.0))
```

A parametrized curve is a curve defined by a function `fun` that maps a (unitless) parameter `t` in the given `range` to a `Point` in space.

## Examples

```julia
ParametrizedCurve(t -> Point(cos(t), sin(t)), (0, 2π))
```
