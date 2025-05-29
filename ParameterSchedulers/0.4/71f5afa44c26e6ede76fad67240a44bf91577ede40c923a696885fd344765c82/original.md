```
TriangleExp{T, S<:Integer}(l0, l1, period, decay)
TriangleExp(; l0, l1, period, decay)
```

A [triangle wave](https://en.wikipedia.org/wiki/Triangle_wave) schedule with `period` and an exponentially decaying amplitude. The output conforms to

```text
abs(l0 - l1) * Triangle(t) * decay^(t - 1) + min(l0, l1)
```

where `Triangle(t)` is `(2 / π) * abs(asin(sin(π * (t - 1) / schedule.period)))` (see [`Triangle`](@ref)).

# Arguments

  * `range == abs(l0 - l1)`: the dynamic range (given by the endpoints)
  * `offset == min(l0, l1)`: the offset / minimum value
  * `period::Integer`: the period
  * `decay`: the decay rate
