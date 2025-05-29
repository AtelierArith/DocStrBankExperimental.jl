```julia
benchmark_differentiation(
    backends,
    scenarios::Vector{<:DifferentiationInterfaceTest.Scenario};
    testset_name,
    benchmark,
    excluded,
    logging,
    count_calls,
    benchmark_test,
    benchmark_seconds,
    benchmark_aggregation,
    adaptive_batchsize
) -> Union{Nothing, DataFrames.DataFrame}

```

Shortcut for [`test_differentiation`](@ref) with only benchmarks and no correctness or type stability checks.

Specifying the set of scenarios is mandatory for this function.
