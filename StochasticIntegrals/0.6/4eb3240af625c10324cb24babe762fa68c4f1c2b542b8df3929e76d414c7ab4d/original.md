```
evolve!(itoprocess::ItoProcess, stochastic::Real, new_time::Real)
```

Evolve the `ItoProcess` forward. This changes the time (`t0`) as well as the `value`.

### Inputs

  * `itoprocess` - The `ItoProcess` to be evolved.
  * `stochastic` - A draw from the `ItoIntegral`.
  * `new_time` - The new time.

### Return

Nothing. It changes the input `ItoProcess`
