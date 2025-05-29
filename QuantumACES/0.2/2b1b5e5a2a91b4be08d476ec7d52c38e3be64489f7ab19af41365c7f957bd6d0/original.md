```
process_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_num::Integer, qiskit_qubit_map::Vector{Int}, experiment_shots::Integer; backend::String = "qiskit", prefix::String = "result")
```

Saves a processed version of saved Qiskit data for the randomised experimental design `d_rand`, produced for example by [`simulate_qiskit_ensemble`](@ref), whose associated ensemble of Qiskit circuits act on `qiskit_qubit_num` qubits and are indexed by the mapping `qiskit_qubit_map`, and which were run with `experiment_shots` shots for each circuit. The saved data is loaded according to the labelling implied by the supplied `backend` and `prefix`.
