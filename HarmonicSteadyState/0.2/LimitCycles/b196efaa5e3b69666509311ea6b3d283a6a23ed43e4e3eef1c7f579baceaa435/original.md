```
get_limit_cycles(
    eom::HarmonicEquation, method::SteadyStateMethod, swept, fixed, ω_lc; kwargs...)
```

Variant of `get_steady_states` for a limit cycle problem characterised by a Hopf frequency (usually called ω_lc)

Solutions with ω_lc = 0 are labelled unphysical since this contradicts the assumption of distinct harmonic variables corresponding to distinct harmonics.
