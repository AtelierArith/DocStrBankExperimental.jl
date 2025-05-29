```
channel_amplitude_damping_generalized(rho::AbstractMatrix, p::Real, γ::Real)
```

Return the Kraus operator representation of the generalized amplitude damping channel. It describes the effect of dissipation to an environment at finite temperature. `γ` is the probability of the system to decay to the ground state. `1-p` can be thought as the energy of the stationary state.
