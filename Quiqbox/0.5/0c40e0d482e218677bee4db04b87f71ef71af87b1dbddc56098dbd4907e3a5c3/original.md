```
optimizeParams!(pbs, bs, nuc, nucCoords, 
                config=POconfig(), N=getCharge(nuc); 
                printInfo=true, infoLevel=1) -> 
Vector{Any}

optimizeParams!(pbs, bs, nuc, nucCoords, 
                N=getCharge(nuc), config=POconfig(); 
                printInfo=true, infoLevel=1) -> 
Vector{Any}
```

The main function to optimize the parameters of a given basis set. It returns a `Vector` of  the relevant information. The first element is the indicator of whether the  optimization is converged if the convergence detection is on (i.e., `config.threshold` is  not `NaN`), or else it's set to `missing`. More elements may be pushed to the returned  result in order depending on `config.method`.

=== Positional argument(s) ===

`pbs::AbstractVector{<:ParamBox{T}}`: The parameters to be optimized that are extracted  from the basis set. If the parameter is marked as "differentiable", the value of its input  variable will be optimized.

`bs::AbstractVector{<:GTBasisFuncs{T, D}}`: The basis set to be optimized.

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: The nuclei in the studied system.

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: The coordinates of corresponding nuclei.

`config::POconfig`: The Configuration of selected parameter optimization method. For more  information please refer to [`POconfig`](@ref).

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: Total number of electrons, or the number(s) of  electrons with same spin configurations(s).

=== Keyword argument(s) ===

`printInfo::Bool`: Whether print out the information of iteration steps.

`infoLevel::Int`: Printed info's level of details when `printInfo=true`. The higher  (the absolute value of) it is, more intermediate steps and other information will be  printed. Once `infoLevel` achieve `5`, every step and all available  information will be printed.
