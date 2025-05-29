```
tiltedtfitrottercircuit(nqubits, n_layers; topology=nothing)
```

Returns a Trottterized circuit for the tilted transverse field Ising model. H = Sum*{(i, i+1) in topology} Z*i Z_{i+1} 

  * Sum*{i=1}^{nqubits} Z*i + Sum*{i=1}^{nqubits} X*i

# Arguments

  * `nqubits::Integer`: The number of qubits in the circuit.
  * `n_layers::Integer`: The number of Trotter steps to perform.
  * `topology=nothing`: The topology of the qubits in the circuit.    Default (nothing): A linear chain.

# Returns

The Trottterized circuit as a vector of Gate.
