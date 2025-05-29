```julia
LinearizationProblem(
    sys::ModelingToolkit.AbstractSystem,
    inputs,
    outputs;
    t,
    kwargs...
) -> ModelingToolkit.LinearizationProblem{F, Float64} where F<:(ModelingToolkit.LinearizationFunction{DI, AI, _A, P, _B, _C, J1, J2, J3, J4, IA, @NamedTuple{abstol::Float64, reltol::Float64, nlsolve_alg::NonlinearSolveFirstOrder.GeneralizedFirstOrderAlgorithm{Missing, NonlinearSolveFirstOrder.GenericTrustRegionScheme{NonlinearSolveFirstOrder.RadiusUpdateSchemes.__Simple, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}}, NonlinearSolveBase.Dogleg{NonlinearSolveBase.NewtonDescent{Nothing}, NonlinearSolveBase.SteepestDescent{Nothing}}, Nothing, Nothing, Nothing, Val{false}}}} where {DI<:AbstractVector{Int64}, AI<:AbstractVector{Int64}, _A, P<:SciMLBase.ODEProblem, _B, _C, J1<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing}}, ModelingToolkit.var"#uff#816"{var"#1489#fun"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#uff#816"), _A, _B}), var"#1489#fun", _A}}, J2<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, _A, _B, _C, ADTypes.AutoForwardDiff{nothing, Nothing}} where {_A, _B, _C}}, J3<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#pff#817"{var"#1490#fun", var"#1491#setter"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#pff#817"), _A, _B}), var"#1490#fun", var"#1491#setter", _A}}, J4<:(ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#hpf#815"{fun, setter}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#hpf#815"), _A, _B}), fun, setter, _A}), IA<:Union{SciMLBase.NoInit, SciMLBase.OverrideInit{Nothing, Nothing, Nothing}}})

```

Construct a `LinearizationProblem` for linearizing the system `sys` with the given `inputs` and `outputs`.

# Keyword arguments

  * `t`: The value of the independent variable

All other keyword arguments are forwarded to `linearization_function`.
