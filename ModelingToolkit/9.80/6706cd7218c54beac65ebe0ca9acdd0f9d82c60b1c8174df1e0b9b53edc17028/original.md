```julia
IntervalNonlinearProblem(
    sys::ModelingToolkit.NonlinearSystem,
    uspan::Tuple{T, T} where T;
    ...
) -> SciMLBase.IntervalNonlinearProblem{false, var"#s182", _A, SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A1, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, _A2}, Base.Pairs{K, V, I, A}, SciMLBase.StandardNonlinearProblem} where {T, var"#s182"<:Tuple{T, T}, _A, _A1, _B, _A2, K, V, I, A}
IntervalNonlinearProblem(
    sys::ModelingToolkit.NonlinearSystem,
    uspan::Tuple{T, T} where T,
    parammap;
    kwargs...
) -> SciMLBase.IntervalNonlinearProblem{false, var"#s182", _A, SciMLBase.IntervalNonlinearFunction{false, SciMLBase.FullSpecialize, ModelingToolkit.GeneratedFunctionWrapper{_A1, _B, Nothing}, Nothing, ModelingToolkit.ObservedFunctionCache{ModelingToolkit.NonlinearSystem}, ModelingToolkit.NonlinearSystem, _A2}, Base.Pairs{K, V, I, A}, SciMLBase.StandardNonlinearProblem} where {T, var"#s182"<:Tuple{T, T}, _A, _A1, _B, _A2, K, V, I, A}

```

Generate an `IntervalNonlinearProblem` from a `NonlinearSystem` and allow for automatically symbolically calculating numerical enhancements.
