```julia
struct PauliFrame{T, S} <: QuantumClifford.AbstractQCState
```

This is a wrapper around a tableau. This "frame" tableau is not to be viewed as a normal stabilizer tableau, although it does conjugate the same under Clifford operations. Each row in the tableau refers to a single frame. The row represents the Pauli operation by which the frame and the reference differ.
