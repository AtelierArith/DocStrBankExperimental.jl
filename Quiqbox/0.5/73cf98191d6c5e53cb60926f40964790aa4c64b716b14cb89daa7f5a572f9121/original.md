```
gradOfHFenergy(par, basis, C, nuc, nucCoords, N=getCharge(nuc)) -> AbstractVector

gradOfHFenergy(par, bs, C, nuc, nucCoords, N=getCharge(nuc)) -> AbstractVector
```

Two methods of `gradOfHFenergy`.

≡≡≡ Positional argument(s) ≡≡≡

`par::AbstractVector{<:ParamBox}`: The parameters for differentiation.

`basis::`[`GTBasis`](@ref)`{T, D} where {T, D}`: Basis set information.

`C::NTuple{<:Any, AbstractMatrix{T}} where T`: The coefficient matrix(s) of the canonical  orbitals with respect to the selected basis set.

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: The nuclei in the studied system.

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: The coordinates of corresponding nuclei.

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: Total number of electrons, or the number(s) of  electrons with same spin configurations(s).

`bs::Union{     NTuple{BN, GTBasisFuncs{T, D, 1}},      AbstractVector{<:GTBasisFuncs{T, D, 1}} } where {T, D}`: A collection of basis functions.

**NOTE:** If any of these two methods is applied, the user needs to make sure the row  orders as well as the colum orders of `C` are consistent with the element order of `bs`  (`basis.basis`). ``
