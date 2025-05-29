```
randomstate(N::Int64; kwargs...)

randomstate(ElT::Type{<: Number}, N::Int64; kwargs...)
```

Generates a random quantum state of N qubits.

Optionally, specify an element type, such as `randomstate(Float64, 10)` for a random real state (by default it is complex).

# Arguments

  * `N`: number of qubits
  * `mixed`: if false (default), generate a random MPS; if true, generates a random LPDO
  * `alg`: algorithm used for initialization: `"rand"` initializes random tensor elements; `"circuit"` initializes with a random quantum circuit (MPS only).
  * `σ`: size of the 0-centered uniform distribution in `alg="rand"`.
  * `χ`: bond dimension of the MPS/LPDO
  * 'ξ`: kraus dimension (LPDO)
  * `normalize`: if true, return normalized state
