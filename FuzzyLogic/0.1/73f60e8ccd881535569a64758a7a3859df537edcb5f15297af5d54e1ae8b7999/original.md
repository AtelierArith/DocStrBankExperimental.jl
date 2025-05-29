```julia
struct PiecewiseLinearMF{T<:Real, S<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Piecewise linear membership function.

### Fields

  * `points::Array{Tuple{T, S}, 1} where {T<:Real, S<:Real}`

### Notes

If the input is between two points, its membership degree is computed by linear interpolation. If the input is before the first point, it has the same membership degree of the first point. If the input is after the last point, it has the same membership degree of the first point.

### Example

```julia
mf = PiecewiseLinearMF([(1, 0), (2, 1), (3, 0), (4, 0.5), (5, 0), (6, 1)])
```
