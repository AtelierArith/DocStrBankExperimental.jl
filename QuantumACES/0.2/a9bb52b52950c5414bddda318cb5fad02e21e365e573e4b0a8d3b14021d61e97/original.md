```
Tableau
```

A tableau representation of a stabiliser state.

Stabiliser circuit simulations follow `Improved simulation of stabilizer circuits` by S. Aaronson and D. Gottesman (2004).

# Fields

  * `tableau::Matrix{Bool}`: The tableau representation of the stabiliser state.
  * `qubit_num::Int16`: The number of qubits in the stabiliser state.
