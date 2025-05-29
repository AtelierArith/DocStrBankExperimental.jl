```
optimise_tuple_set(d::Design, covariance_log::SparseMatrixCSC{Float64, Int}; options::OptimOptions = OptimOptions())
```

Returns versions of the design `d` and circuit log-eigenvalue estimator covariance matrix `covariance_log` after optimising the tuple set of the design with repeated excursions that grow and prune the tuple set. The optimisation is parameterised by the [`OptimOptions`](@ref) object `options`.
