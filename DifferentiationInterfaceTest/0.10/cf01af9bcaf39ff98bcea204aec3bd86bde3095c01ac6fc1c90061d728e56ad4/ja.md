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

[`test_differentiation`](@ref) のショートカットで、ベンチマークのみで正確性や型の安定性チェックはありません。

この関数にはシナリオのセットを指定することが必須です。
