A random Pauli operator on n qubits.

Use `nophase=false` to randomize the phase. Use `realphase=false` to get operators with phases including ±i.

Optionally, a "flip" probability `p` can be provided specified, in which case each bit is set to I with probability `1-p` and to X or Y or Z with probability `p`. Useful for simulating unbiased Pauli noise.

See also [`random_pauli!`](@ref)
