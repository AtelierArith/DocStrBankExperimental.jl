```
MaskedPauliRotation(symbols::Vector{Symbol}, qinds::Vector{Int}, term::PauliStringType)
```

A parametrized Pauli rotation gate acting on the qubits `qinds` with the Pauli string `symbols`. The `term` is the integer representation of the Pauli string with the correct integer type for the total number of qubits. This allows for faster application of the gate. See `tomaskedpaulirotation` for conversion from `PauliRotation`, which is the easiest way to construct a `MaskedPauliRotation`.
