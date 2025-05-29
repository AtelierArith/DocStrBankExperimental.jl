```
LineIntegralGaugeField <: AbstractField
```

A gauge field defined by a line integral function.

---

```
LineIntegralGaugeField(func)
```

Create a gauge field with a given line integral function `func`. The function should take two points in space and return the line integral of the vector potential between these points.

## Example

```julia
field = LineIntegralGaugeField() do p1, p2
    0.5 * (p1[1] * p2[2] - p1[2] * p2[1])   # A = [-y/2, x/2, 0]
end
```
