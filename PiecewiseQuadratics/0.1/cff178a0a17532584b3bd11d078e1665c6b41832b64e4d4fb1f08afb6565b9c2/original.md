```
Interval(lb::Real, ub::Real)
```

Represents a univariate interval.

The fields represent:

  * `lb`: Lower bound of the interval
  * `ub`: Upper bound of the interval

# Example

```jldoctest
julia> interval = Interval(0., 1.)
[0.00000, 1.00000]

julia> Interval()
ℝ

```
