```
GaugeField <: AbstractField
```

A gauge field defined by a vector potential function.

---

```
GaugeField(func; n)
```

Create a gauge field with a given vector potential function `func`.

## Arguments

  * `func`: a function that takes a point in space and returns the vector potential at this point as a `SVector` or `Tuple`.
  * `n`: the number of steps to use in the trapezoidal rule integration.

## Example

```julia
field = GaugeField(n = 10) do p
    (-0.5 * p[2], 0.5 * p[1], 0)
end
```
