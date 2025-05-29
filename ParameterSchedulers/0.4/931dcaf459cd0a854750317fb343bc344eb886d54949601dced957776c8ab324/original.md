```
SinExp(l0, l1, period, decay)
SinExp(; l0, l1, period, decay)
```

A sine wave schedule with `period` and an exponentially decaying amplitude. The output conforms to

```text
abs(l0 - l1) * Sin(t) * γ^(t - 1) + min(l0, l1)
```

where `Sin(t)` is `abs(sin(π * (t - 1) / period))` (see [`Sin`](@ref)).

# Arguments

  * `range == abs(l0 - l1)`: the dynamic range (given by the endpoints)
  * `offset == min(l0, l1)`: the offset / minimum value
  * `period::Integer`: the period
  * `decay`: the decay rate
