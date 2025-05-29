```
ShiftingField <: Hamiltonian
ShiftingField(magnitude::Union{Field, TimeSeries}) -> ShiftingField
```

Represents a shifting field in a [`Hamiltonian`](@ref) which changes the energy of the Rydberg level in  an [`AnalogHamiltonianSimulation`](@ref).

$$
H_{sf}(t) = - \Delta(t) \sum_k h_k \left| r_k \right\rangle\left\langle r_k \right|
$$

Where $\left| r_k \right\rangle$ is the Rydberg state of atom $k$, and $h_k$ is the local pattern of unitless real numbers between 0 and 1.

The argument `magnitude` represents the global magnitude time series $\Delta(t)$, where time is in units of seconds and values are in units of radians / second.
