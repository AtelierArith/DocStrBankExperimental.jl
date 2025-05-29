```
struct ErrorModel
```

This struct  holds all of the information used to simulate coherent noise, incoherent noise, and readout error for a specific error model. The structure is as follows:

# Arguments

  * `confusion_mat`: Function to generate a confusion matrix given a number of qubits,

with type `(Int)->(T)` where `T`` is Matrix-like

  * `collapse_ops`: Function to generate the collapse operators given a number of qubits, with type

`(Int)->Vector{SparseMatrixCSC}`

  * `coherent_noise`: Function returning a function that generates random samples from a Hamiltonian

with type `(RydbergHamiltonian)->(()->RydbergHamiltonian)`
