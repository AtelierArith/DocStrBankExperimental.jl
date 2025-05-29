```julia
get_looptransfer_function(
    sys::ModelingToolkit.AbstractSystem,
    aps;
    kwargs...
) -> Tuple{ModelingToolkit.LinearizationFunction{DI, AI, _A, P, _B, _C, J1, J2, J3, J4, IA, @NamedTuple{abstol::Float64, reltol::Float64, nlsolve_alg::NonlinearSolveFirstOrder.GeneralizedFirstOrderAlgorithm{Missing, NonlinearSolveFirstOrder.GenericTrustRegionScheme{NonlinearSolveFirstOrder.RadiusUpdateSchemes.__Simple, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}}, NonlinearSolveBase.Dogleg{NonlinearSolveBase.NewtonDescent{Nothing}, NonlinearSolveBase.SteepestDescent{Nothing}}, Nothing, Nothing, Nothing, Val{false}}}} where {DI<:AbstractVector{Int64}, AI<:AbstractVector{Int64}, _A, P<:SciMLBase.ODEProblem, _B, _C, J1<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing}}, ModelingToolkit.var"#uff#846"{var"#1535#fun"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#uff#846"), _A, _B}), var"#1535#fun", _A}}, J2<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, _A, _B, _C, ADTypes.AutoForwardDiff{nothing, Nothing}} where {_A, _B, _C}}, J3<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#pff#847"{var"#1536#fun", var"#1537#setter"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#pff#847"), _A, _B}), var"#1536#fun", var"#1537#setter", _A}}, J4<:(ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#hpf#845"{fun, setter}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#hpf#845"), _A, _B}), fun, setter, _A}), IA<:Union{SciMLBase.NoInit, SciMLBase.OverrideInit{Nothing, Nothing, Nothing}}}, Any}

```

Return the loop-transfer function for the analysis point(s) `aps`, and the modified system simplified with the appropriate inputs and outputs.

# Keyword Arguments

```
- `loop_openings`: A list of analysis points whose connections should be removed and
  the outputs set to zero as a part of the linear analysis.

- `system_modifier`: A function taking the transformed system and applying any
  additional transformations, returning the modified system. The modified system
  is passed to `linearization_function`.
```

All other keyword arguments are forwarded to `linearization_function`.
