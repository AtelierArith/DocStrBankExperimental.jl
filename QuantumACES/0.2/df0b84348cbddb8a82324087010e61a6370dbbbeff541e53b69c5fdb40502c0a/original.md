```
estimate_qiskit_ensemble(d_rand::RandDesign, qiskit_qubit_map::Vector{Int}, experiment_shots::Integer; fail_jobs::Vector{Int} = Int[], backend::String = "qiskit", ls_type::Symbol = :fgls, split::Bool = false, min_eigenvalue::Real = 0.1)
```

Returns estimated circuit eigenvalues, and gate noise estimates from Qiskit data processed with [`process_qiskit_ensemble`] for the randomised experimental design `d_rand` with `experiment_shots` shots per circuit. Avoids attempting to load failed jobs specified by `fail_jobs`. The simulated data is loaded according to the label implied by the supplied `backend`, and the estimation procedure uses the least squares estimator `ls_type`, splitting the gate eigenvalue estimator projection across the gates if `split` is `true`, and includes only circuit eigenvalues which are at least `min_eigenvalue`.
