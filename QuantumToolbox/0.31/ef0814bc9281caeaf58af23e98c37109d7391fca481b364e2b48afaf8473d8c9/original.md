```
lr_mesolveProblem(
    H::QuantumObject{Operator},
    z::AbstractArray{T,2},
    B::AbstractArray{T,2},
    tlist::AbstractVector,
    c_ops::Union{AbstractVector,Tuple}=();
    e_ops::Union{AbstractVector,Tuple}=(),
    f_ops::Union{AbstractVector,Tuple}=(),
    opt::NamedTuple = lr_mesolve_options_default,
    kwargs...,
)
```

Formulates the ODEproblem for the low-rank time evolution of the system. The function is called by [`lr_mesolve`](@ref). For more information about the low-rank master equation, see [gravina2024adaptive](@cite).

# Arguments

  * `H::QuantumObject`: The Hamiltonian of the system.
  * `z::AbstractArray`: The initial z matrix of the low-rank algorithm.
  * `B::AbstractArray`: The initial B matrix of the low-rank algorithm.
  * `tlist::AbstractVector`: The time steps at which the expectation values and function values are calculated.
  * `c_ops::Union{AbstractVector,Tuple}`: The list of the collapse operators.
  * `e_ops::Union{AbstractVector,Tuple}`: The list of the operators for which the expectation values are calculated.
  * `f_ops::Union{AbstractVector,Tuple}`: The list of the functions for which the function values are calculated.
  * `opt::NamedTuple`: The options of the low-rank master equation.
  * `kwargs`: Additional keyword arguments.
