```
Design
```

Experimental design for a noise characterisation experiment for a circuit.

# Fields

  * `c::AbstractCircuit`: Circuit characterised by the design.
  * `full_covariance::Bool`: If `true`, generates parameters to construct the full covariance matrix in `covariance_dict_ensemble`, else if `false`, only generates parameters to construct the terms on the diagonal.
  * `matrix::SparseMatrixCSC{Int32, Int32}`: Sparse M x N design matrix, corresponding to M circuit eigenvalues and N gate eigenvalues.
  * `tuple_set::Vector{Vector{Int}}`: Set of tuples which arrange the circuit layers.
  * `tuple_set_data::TupleSetData`: [`TupleSetData`](@ref) object that generates the tuple set.
  * `mapping_ensemble::Vector{Vector{Mapping}}`: Vector of the [`Mapping`](@ref) objects for each of the circuit eigenvalue for the Paulis corresponding to that tuple, for each tuple in the set.
  * `experiment_ensemble::Vector{Vector{Vector{Int}}}`: Vector of the experiments that index [`Mapping`](@ref) objects, which correspond to simultaneously preparable and measurable circuit eigenvalues, for each tuple in the set.
  * `covariance_dict_ensemble::Vector{Dict{CartesianIndex{2}, Tuple{Mapping, Int}}}`: Dictionary of [`Mapping`](@ref) objects describing the non-zero entries of the sparse circuit eigenvalue estimator covariance matrix, alongside the number of times the entry is estimated by the experiment set, for each tuple in the set.
  * `prep_ensemble::Vector{Vector{Layer}}`: Vector of [`Layer`](@ref) objects that prepare qubits in Pauli eigenstates for each experiment in the set, for each tuple in the set.
  * `meas_ensemble::Vector{Vector{Layer}}`: Vector of [`Layer`](@ref) objects that measure qubits in Pauli bases for each experiment in the set, for each tuple in the set.
  * `tuple_times::Vector{Float64}`: Time taken to implement the circuit arranged by each tuple in the set, normalised according to the time factor for the basic tuple set.
  * `shot_weights::Vector{Float64}`: Shot weights for each tuple in the set, which add to 1.
  * `experiment_numbers::Vector{Int}`: Number of experiments for each tuple in the set.
  * `experiment_number::Int`: Total number of experiments.
  * `calculation_times::Matrix{Float64}`: Time taken to generate components of the design for each tuple, which correspond to generating: the mappings, the sets of tuple-consistent Pauli preparations, the experiment sets, and the covariance matrix dictionary.
  * `overall_time::Float64`: Overall time taken to generate the design.
  * `optimisation_time::Float64`: Time taken to optimise the design.
  * `ls_type::Symbol`: Type of least squares for which the shot weights were optimised.
