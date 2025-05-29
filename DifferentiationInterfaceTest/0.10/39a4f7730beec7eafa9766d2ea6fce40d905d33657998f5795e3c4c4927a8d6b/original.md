```
DifferentiationBenchmarkDataRow
```

Ad-hoc storage type for differentiation benchmarking results.

# Fields

  * `backend::ADTypes.AbstractADType`: backend used for benchmarking
  * `scenario::DifferentiationInterfaceTest.Scenario`: scenario used for benchmarking
  * `operator::Symbol`: differentiation operator used for benchmarking, e.g. `:gradient` or `:hessian`
  * `prepared::Union{Nothing, Bool}`: whether the operator had been prepared
  * `calls::Int64`: number of calls to the differentiated function for one call to the operator
  * `samples::Int64`: number of benchmarking samples taken
  * `evals::Int64`: number of evaluations used for averaging in each sample
  * `time::Any`: aggregated runtime over all samples, in seconds
  * `allocs::Any`: aggregated number of allocations over all samples
  * `bytes::Any`: aggregated memory allocated over all samples, in bytes
  * `gc_fraction::Any`: aggregated fraction of time spent in garbage collection over all samples, between 0.0 and 1.0
  * `compile_fraction::Any`: aggregated fraction of time spent compiling over all samples, between 0.0 and 1.0

See the documentation of [Chairmarks.jl](https://github.com/LilithHafner/Chairmarks.jl) for more details on the measurement fields.
