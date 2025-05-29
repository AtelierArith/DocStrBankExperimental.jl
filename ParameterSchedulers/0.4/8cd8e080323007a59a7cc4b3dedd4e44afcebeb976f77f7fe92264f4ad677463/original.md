```
SinDecay2(l0, l1, period)
SinDecay2(; l0, l1, period)
```

A sine wave schedule with `period` and half the amplitude each cycle. The output conforms to

```text
abs(l0 - l1) * Sin(t) / (2^floor((t - 1) / period)) + min(l0, l1)
```

where `Sin(t)` is `abs(sin(π * (t - 1) / period))` (see [`Sin`](@ref)).

# Arguments

  * `range == abs(l0 - l1)`: the dynamic range (given by the endpoints)
  * `offset == min(l0, l1)`: the offset / minimum value
  * `period::Integer`: the period
