```
RandDesign
```

Pauli frame randomised experimental ensemble for an experimental design.

# Fields

  * `d::Design`: Experimental design.
  * `pauli_randomisation_ensemble::Vector{Vector{Vector{Vector{String}}}}`: For each tuple, experiment, and randomisation, a vector of Pauli frame randomisations between each layer in the randomised circuit.
  * `pauli_sign_ensemble::Vector{Vector{Vector{Vector{Bool}}}}`: For each tuple, experiment, and randomisation, a vector of signs for the Paulis estimated by the randomised experiment.
  * `covariance_pauli_sign_ensemble::Vector{Vector{Vector{Vector{Bool}}}}`: For each tuple, experiment, and randomisation, a vector of signs for the covariance Paulis estimated by the randomised experiment.
  * `job_indices::Vector{Vector{NTuple{3, Int}}}`: For each job, a vector of indices (tuple, experiment, randomisation) for each circuit in the job.
  * `randomisations::Vector{Int}`: Number of randomisations for the experiment set corresponding to each tuple in the design.
  * `shot_budget::Int`: Shot budget for the randomised experimental ensemble.
  * `experiment_shots::Int`: Number of shots for each experiment in the randomised experimental ensemble.
  * `seed::UInt64`: Random seed used to generate the randomised experimental ensemble.
