```
calcPhaseDiagram(H::Function, param_range1::T1, param_range2::T2, alg::T3; N::T4=51, parallel::T5=UseSingleThread(), gapless::Real=0.0, rounds::Bool=true, plot::Bool=false, progress::Bool=false) where {T1<:AbstractVector,T2<:AbstractVector,T3<:Union{String,TopologicalNumbersAlgorithms},T4<:Union{Int,Tuple,AbstractVector},T5<:TopologicalNumbersParallel}
```
