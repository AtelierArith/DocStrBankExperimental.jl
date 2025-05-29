```
white_noise!(ρ::AbstractMatrix, v::Real)
```

Modifies `ρ` in place to tranform it into `v * rho + (1 - v) * id` where `id` is the maximally mixed state.
