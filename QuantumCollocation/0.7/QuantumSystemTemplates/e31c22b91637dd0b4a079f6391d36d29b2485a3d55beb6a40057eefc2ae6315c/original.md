```
TransmonDipoleCoupling(
    g_ij::Float64,
    pair::Tuple{Int, Int},
    subsystem_levels::Vector{Int};
    lab_frame::Bool=false,
) -> QuantumSystemCoupling

TransmonDipoleCoupling(
    g_ij::Float64,
    pair::Tuple{Int, Int},
    sub_systems::Vector{QuantumSystem};
    kwargs...
) -> QuantumSystemCoupling
```

Returns a `QuantumSystemCoupling` object for a transmon qubit. In the lab frame, the Hamiltonian coupling term is

$$
H = g_{ij} (a_i + a_i^\dagger) (a_j + a_j^\dagger)
$$

In the rotating frame, the Hamiltonian coupling term is

$$
H = g_{ij} (a_i a_j^\dagger + a_i^\dagger a_j)
$$

where `a_i` is the annihilation operator for the `i`th transmon.
