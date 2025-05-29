```
TransmonSystem(;
    ω::Float64=4.4153,  # GHz
    δ::Float64=0.17215, # GHz
    levels::Int=3,
    lab_frame::Bool=false,
    frame_ω::Float64=ω,
) -> QuantumSystem
```

Returns a `QuantumSystem` object for a transmon qubit, with the Hamiltonian

$$
H = \omega a^\dagger a - \frac{\delta}{2} a^\dagger a^\dagger a a
$$

where `a` is the annihilation operator.

# Keyword Arguments

  * `ω`: The frequency of the transmon, in GHz.
  * `δ`: The anharmonicity of the transmon, in GHz.
  * `levels`: The number of levels in the transmon.
  * `lab_frame`: Whether to use the lab frame Hamiltonian, or an ω-rotating frame.
  * `frame_ω`: The frequency of the rotating frame, in GHz.
  * `mutiply_by_2π`: Whether to multiply the Hamiltonian by 2π, set to true by default because the frequency is in GHz.
  * `lab_frame_type`: The type of lab frame Hamiltonian to use, one of (:duffing, :quartic, :cosine).
  * `drives`: Whether to include drives in the Hamiltonian.
