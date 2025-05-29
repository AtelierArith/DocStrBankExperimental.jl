```
randomcircuit(
  coupling_sequence::Vector;
  depth::Int = 1,
  twoqubitgates::Union{String,Vector{String}}="RandomUnitary",
  onequbitgates::Union{Nothing,String,Vector{String}}=nothing,
  layered::Bool=true,
  rng=Random.GLOBAL_RNG)
```

Build a circuit with given `depth`, where each layer consists of a set of two-qubit gates applied on pairs of qubits in according to a set of `coupling_sequences`. Each layer also contains $n$ single-qubit gates. IN both cases, the chosen gates are passed as keyword arguments `onequbitgates` and `twoqubitgates`.

The default configurations consists of two-qubit random Haar unitaries, and no single-qubit gates.

If `layered = true`, the object returned in a `Vector` of circuit layers, rather than the full collection  of quantum gates.
