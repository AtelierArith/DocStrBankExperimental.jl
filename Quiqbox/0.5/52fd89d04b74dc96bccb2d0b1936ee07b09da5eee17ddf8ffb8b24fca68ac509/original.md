```
GDconfig{T, M, ST<:Union{Array{T, 0}, T}} <: ConfigBox{T, GDconfig, M}
```

The mutable container of configurations for the default gradient descent method used to  optimize parameters.

≡≡≡ Field(s) ≡≡≡

`lineSearchMethod::M`: The selected line search method to optimize the step size for each  gradient descent iteration. It can be any algorithm defined in the Julia package  [LineSearches.jl](https://github.com/JuliaNLSolvers/LineSearches.jl), or [`itself`](@ref)  so that the step size will be fixed to a constant value during all the iterations.

`initialStep::ST`: The value of the initial step size in each iteration. If it's an  `Array{T, 0}`, then the final step size (optimized by `lineSearchMethod`) in current  interaction will be set as the initial step size for the next iteration.

`stepBound::NTuple{2, T}`: The lower bound and upper bound of the step size to enforce  `stepBound[begin] ≤ η ≤ stepBound[end]` (where `η` is the step size in each iteration).  Whenever the size size is out of the boundary, it will be clipped to a bound value.

`scaleStepBound::Bool`: Determine whether `stepBound` will be scaled so that the norm of  the gradient descent in each iteration is constrained within the initially configured  `stepBound`, i.e., `stepBound[begin] ≤ norm(η*∇f) ≤ stepBound[end]` (where `∇f` is the  gradient of some function `f` in each iteration).

≡≡≡ Initialization Method(s) ≡≡≡

```
GDconfig(lineSearchMethod::M=BackTracking(), 
         initialStep::Union{Array{T, 0}, T}=ifelse(M==typeof(Quiqbox.itself), 0.1, 1.0); 
         stepBound::NTuple{2, T}=convert.(eltype(initialStep), (0, Inf)), 
         scaleStepBound::Bool=ifelse(M==typeof(itself), true, false)) where 
        {M, T<:AbstractFloat} -> 
GDconfig{T, M, typeof(initialStep)}
```
