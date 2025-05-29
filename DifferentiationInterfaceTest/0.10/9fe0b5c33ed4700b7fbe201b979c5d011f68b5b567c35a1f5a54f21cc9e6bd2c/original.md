```julia
test_differentiation(
    backends::Vector{<:ADTypes.AbstractADType};
    ...
) -> Union{Nothing, DataFrames.DataFrame}
test_differentiation(
    backends::Vector{<:ADTypes.AbstractADType},
    scenarios::Vector{<:DifferentiationInterfaceTest.Scenario};
    testset_name,
    correctness,
    type_stability,
    allocations,
    benchmark,
    excluded,
    detailed,
    logging,
    isapprox,
    atol,
    rtol,
    scenario_intact,
    sparsity,
    reprepare,
    ignored_modules,
    function_filter,
    skip_allocations,
    count_calls,
    benchmark_test,
    benchmark_seconds,
    benchmark_aggregation,
    adaptive_batchsize
) -> Union{Nothing, DataFrames.DataFrame}

```

Apply a list of `backends` on a list of `scenarios`, running a variety of different tests and/or benchmarks.

# Return

This function always creates and runs a `@testset`, though its contents may vary.

  * if `benchmark == :none`, it returns `nothing`.
  * if `benchmark != :none`, it returns a `DataFrame` of benchmark results, whose columns correspond to the fields of [`DifferentiationBenchmarkDataRow`](@ref).

# Positional arguments

  * `backends::Vector{<:AbstractADType}`: the backends to test
  * `scenarios::Vector{<:Scenario}`: the scenarios on which to test these backends. Defaults to a standard set of first- and second-order scenarios, whose contents are not part of the public API and may change without notice.

# Keyword arguments

  * `testset_name=nothing`: how to display the test set

**Test categories:**

  * `correctness=true`: whether to compare the differentiation results with the theoretical values specified in each scenario
  * `type_stability=:none`: whether (and how) to check type stability of operators with JET.jl.
  * `allocations=:none`: whether (and how) to check allocations inside operators with AllocCheck.jl
  * `benchmark=:none`: whether (and how) to benchmark operators with Chairmarks.jl

For `type_stability`, `allocations` and `benchmark`, the possible values are `:none`, `:prepared` or `:full`. Each setting tests/benchmarks a different subset of calls:

|       kwarg | prepared operator | unprepared operator | preparation |
| -----------:| -----------------:| -------------------:| -----------:|
|     `:none` |                no |                  no |          no |
| `:prepared` |               yes |                  no |          no |
|     `:full` |               yes |                 yes |         yes |

**Misc options:**

  * `excluded::Vector{Symbol}`: list of operators to exclude, such as [`FIRST_ORDER`](@ref) or [`SECOND_ORDER`](@ref)
  * `detailed=false`: whether to create a detailed or condensed testset
  * `logging=false`: whether to log progress

**Correctness options:**

  * `isapprox=isapprox`: function used to compare objects approximately, with the standard signature `isapprox(x, y; atol, rtol)`
  * `atol=0`: absolute precision for correctness testing (when comparing to the reference outputs)
  * `rtol=1e-3`: relative precision for correctness testing (when comparing to the reference outputs)
  * `scenario_intact=true`: whether to check that the scenario remains unchanged after the operators are applied
  * `sparsity=false`: whether to check sparsity patterns for Jacobians / Hessians
  * `reprepare::Bool=true`: whether to modify preparation before testing when the preparation arguments have the wrong size

**Type stability options:**

  * `ignored_modules=nothing`: list of modules that JET.jl should ignore
  * `function_filter`: filter for functions that JET.jl should ignore (with a reasonable default)

**Benchmark options:**

  * `count_calls=true`: whether to also count function calls during benchmarking
  * `benchmark_test=true`: whether to include tests which succeed iff benchmark doesn't error
  * `benchmark_seconds=1`: how long to run each benchmark for
  * `benchmark_aggregation=minimum`: function used to aggregate sample measurements

**Batch size options**

  * `adaptive_batchsize=true`: whether to cap the backend's preset batch size (when it exists) to prevent errors on small inputs
