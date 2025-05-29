```
coherentthermalstate(v::VibrationalMode, n̄::Real, α::Number; method="truncated)
```

Returns a displaced thermal state for `v`, which is created by applying a displacement operation to a thermal state. The mean occupation of the thermal state is `n̄` and `α` is the complex amplitude of the displacement.

`method` can be either `"truncated"` or `"analytic"` and this argument determines how the displacement operator is computed (see: [`displace`](@ref)) .
