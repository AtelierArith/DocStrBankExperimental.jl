A Stabilizer measurement on the entirety of the quantum register.

`projectrand!(state, pauli)` and `apply!(state, PauliMeasurement(pauli))` give the same (possibly non-deterministic) result. Particularly useful when acting on [`Register`](@ref).

See also: [`apply!`](@ref), [`projectrand!`](@ref).
