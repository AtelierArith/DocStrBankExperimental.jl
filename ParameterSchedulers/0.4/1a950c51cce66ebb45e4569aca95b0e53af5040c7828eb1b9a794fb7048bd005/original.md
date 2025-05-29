```
Sin(l0, l1, period)
Sin(; l0, l1, period)
```

A sine wave schedule with `period`. The output conforms to

```text
abs(l0 - l1) * abs(sin(π * (t - 1) / period)) + min(l0, l1)
```

# Arguments

  * `range == abs(l0 - l1)`: the dynamic range (given by the endpoints)
  * `offset == min(l0, l1)`: the offset / minimum value
  * `period::Integer`: the period
