```
mirror_symmetric_qubit_states( θ ::  Real ) :: Vector{State{Float64}}
```

Returns a set of 3 mirror symmetric qubit density matrices. The first state is $|0\rangle\langle 0|$ the other two are symmetric about the  $|0\rangle$ axis. See [`mirror_symmetric_qubit_kets`](@ref).

Input:

  * `θ ∈ [0,π/2]`: the hilbert space angle between $|0\rangle$ and $|\psi_{2/3}\rangle$.
