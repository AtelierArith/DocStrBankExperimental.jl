```
run_speed_test(m::EFTfitterModel; matrix_types=[Matrix, sparse, Symmetric], vs=rand(m.parameters, 10), verbose=true)
```

Test different data types for the (inverse) covariance matrix to find the optimal one in terms of speed.

# Arguments

  * `m::EFTfitterModel`: The model for which the speed test is performed.

# Keyword Arguments

  * `matrix_types::Vector{DataType}=[Matrix, sparse, Symmetric]`: The types of matrices to be tested.
  * `vs`: Sample values to test. Default is 10 random samples from `m.parameters`.
  * `verbose::Bool=true`: If `true`, informative messages and results are displayed during the test.

# Returns

  * A table summarizing the test results, showing minimum computation times, memory allocations, etc., for each matrix type.
  * A list of benchmark results for each matrix type.

Notes

The function benchmarks the provided matrix types using the given sample values and returns recommendations based on minimum computation times. The recommended matrix type is the one with the shortest minimum time.

# Example

```julia-repl
julia> tbl, benchmarks = run_speed_test(model)
```
