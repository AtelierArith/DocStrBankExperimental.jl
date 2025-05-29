```
UniformCircular(domain=2π)
```

Creates a variable parameterized on a continuous, periodic domain. Creates two normally diastributed random variables :Ωx and :Ωy  and maps them to a circular domain using a derived variable  according to `atan(:Ωy, :Ωx)`. This may be more efficient than using e.g. `Ω = Uniform(-pi, pi)` because the sampler can wrap around freely.

Example:

```julia
Variables(;
    a = Uniform(1, 10),
    e = Uniform(0, 1),
    UniformCircular(:Ω)...,
)
```
