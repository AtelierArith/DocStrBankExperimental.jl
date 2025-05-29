```julia
LinearizationProblem(
    sys::ModelingToolkit.AbstractSystem,
    inputs,
    outputs;
    t,
    kwargs...
) -> ModelingToolkit.LinearizationProblem{F, Float64} where F<:(ModelingToolkit.LinearizationFunction{DI, AI, _A, P, _B, _C, J1, J2, J3, J4, IA, @NamedTuple{abstol::Float64, reltol::Float64, nlsolve_alg::NonlinearSolveFirstOrder.GeneralizedFirstOrderAlgorithm{Missing, NonlinearSolveFirstOrder.GenericTrustRegionScheme{NonlinearSolveFirstOrder.RadiusUpdateSchemes.__Simple, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}, Rational{Int64}}, NonlinearSolveBase.Dogleg{NonlinearSolveBase.NewtonDescent{Nothing}, NonlinearSolveBase.SteepestDescent{Nothing}}, Nothing, Nothing, Nothing, Val{false}}}} where {DI<:AbstractVector{Int64}, AI<:AbstractVector{Int64}, _A, P<:SciMLBase.ODEProblem, _B, _C, J1<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing}}, ModelingToolkit.var"#uff#846"{var"#1535#fun"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#uff#846"), _A, _B}), var"#1535#fun", _A}}, J2<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, _A, _B, _C, ADTypes.AutoForwardDiff{nothing, Nothing}} where {_A, _B, _C}}, J3<:Union{Nothing, ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#pff#847"{var"#1536#fun", var"#1537#setter"}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#pff#847"), _A, _B}), var"#1536#fun", var"#1537#setter", _A}}, J4<:(ModelingToolkit.PreparedJacobian{true, DifferentiationInterfaceForwardDiffExt.ForwardDiffTwoArgJacobianPrep{Nothing, C, Tuple{Nothing, Nothing, Nothing}}, ModelingToolkit.var"#hpf#845"{fun, setter}, _A, ADTypes.AutoForwardDiff{nothing, Nothing}} where {C<:(ForwardDiff.JacobianConfig{T, _A, _B, <:Tuple{Any, Any}} where {T<:(ForwardDiff.Tag{F} where F<:ModelingToolkit.var"#hpf#845"), _A, _B}), fun, setter, _A}), IA<:Union{SciMLBase.NoInit, SciMLBase.OverrideInit{Nothing, Nothing, Nothing}})

```

システム `sys` を与えられた `inputs` と `outputs` で線形化するための `LinearizationProblem` を構築します。

# キーワード引数

  * `t`: 独立変数の値

他のすべてのキーワード引数は `linearization_function` に渡されます。
