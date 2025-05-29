```
DrivingField <: Hamiltonian
DrivingField(amplitude::Union{Field, TimeSeries}, phase::Union{Field, TimeSeries}, detuning::Union{Field, TimeSeries}) -> DrivingField
```

Represents a driving field in a [`Hamiltonian`](@ref) which coherently transfers atoms from the ground state to the Rydberg state in an [`AnalogHamiltonianSimulation`](@ref).

$$
H_{df}(t) = \frac{1}{2} \Omega(t)\exp(i \phi(t)) \sum_k \left( | g_k \rangle\langle r_k | + h.c.\right) - \Delta(t) \sum_k| r_k \rangle\langle r_k |
$$

Where $\left| g_k \right\rangle$ is the ground state of atom $k$ and $\left| r_k \right\rangle$ is the Rydberg state of atom $k$.

# Arguments

  * `amplitude` represents the global amplitude $\Omega(t)$. The time is in units of seconds, and the value is in radians/second.
  * `phase` represents the global phase $\phi(t)$. The time is in units of seconds, and the value is in radians/second.
  * `detuning` represents the global detuning $\Delta(t)$. The time is in units of seconds, and the value is in radians/second.
