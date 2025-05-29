```
simulate_qiskit_ensemble(d_rand::RandDesign, qiskit_ensemble::Py, experiment_shots::Integer; backend::String = "qiskit", prefix::String = "result", simulator::Py = aer.AerSimulator(; method = "stabilizer"), diagnostics::Bool = true)
```

Saves data simulated with Qiskit for the randomised experimental design `d_rand` with an associated ensemble of Qiskit circuits `qiskit_ensemble` produced by [`get_stim_qiskit_ensemble`](@ref), with `experiment_shots` shots for each circuit. The saved data is labelled according to the supplied `backend` and `prefix`, and simulated using the supplied `simulator`, displaying diagnostics if `diagnostics` is `true.
