```julia
TrustRegionSolver(
    objective::Cthonios.AbstractObjective,
    p,
    timer;
    preconditioner,
    use_warm_start,
    settings
) -> Cthonios.TrustRegionSolver{L, O, Vector{Float64}, W, TimerOutputs.TimerOutput, F, Cthonios.TrustRegionSolverSettings} where {L<:(Cthonios.CholeskyPreconditioner{A, SparseArrays.CHOLMOD.Factor{Float64, Int64}} where A<:(FiniteElementContainers.StaticAssembler{Float64, Int64, _A, _B, _C, _D, _E, _F, _G, _H, _I, _J, _K, Vector{Int64}, Vector{Int64}, Vector{Float64}} where {_A<:AbstractVector{Int64}, _B<:AbstractVector{Int64}, _C<:AbstractVector{Int64}, _D<:AbstractVector{Int64}, _E<:AbstractVector{Int64}, _F<:FiniteElementContainers.NodalField, _G<:AbstractVector{Float64}, _H, _I, _J, _K})), O<:Cthonios.AbstractObjective, W<:Union{Cthonios.WarmStart{R} where R<:(FiniteElementContainers.SimpleNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractMatrix{_A}}), Cthonios.WarmStart{R} where R<:(FiniteElementContainers.VectorizedNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractVector{_A}})}, F<:Union{FiniteElementContainers.SimpleNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractMatrix{_A}}, FiniteElementContainers.VectorizedNodalField{_A, 2, _B, _C, A} where {_A<:Number, _B, _C, A<:AbstractVector{_A}}}}

```

TODO どのスクラッチ配列を削除できるかを考える
