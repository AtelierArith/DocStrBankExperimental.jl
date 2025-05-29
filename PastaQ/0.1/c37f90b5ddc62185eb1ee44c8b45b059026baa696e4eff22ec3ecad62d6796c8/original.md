```
randomprocess(N::Int64; kwargs...)

randomprocess(ElT::Type{<: Number}, N::Int64; kwargs...)
```

Generates a random quantum procecss of N qubits.

Optionally choose the element type with calls like `randomprocess(Float64, 10)` (by default it is complex).

# Arguments

  * `N`: number of qubits
  * `mixed`: if false (default), generates a random MPO; if true, generates a random LPDO.
  * `alg`: initialization criteria, set to `"randompars"` (see `randomstate`).
  * `σ`: size of the 0-centered uniform distribution in `alg="rand"`.
  * `χ`: bond dimension of the MPO/LPDO.
  * 'ξ`: kraus dimension (LPDO).
