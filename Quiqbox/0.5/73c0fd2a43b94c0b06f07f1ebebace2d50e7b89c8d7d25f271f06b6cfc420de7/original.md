```
runHF(bs, nuc, nucCoords, config=HFconfig(), N=getCharge(nuc); 
      printInfo=true, infoLevel=2) -> 
HFfinalVars

runHF(bs, nuc, nucCoords, N=getCharge(nuc), config=HFconfig(); 
      printInfo=true, infoLevel=2) -> 
HFfinalVars
```

Main function to run a Hartree–Fock method in Quiqbox. The returned result and relevant  information is stored in a [`HFfinalVars`](@ref).

```
runHFcore(args...; printInfo=false, infoLevel=2) -> 
Tuple{Tuple{Vararg{HFtempVars}}, Bool}
```

The core function of `runHF` that accept the same positional arguments as `runHF`, except  it returns the data (`HFtempVars`) collected during the iteration and the boolean result of  whether the SCF procedure is converged.

≡≡≡ Positional argument(s) ≡≡≡

`bs::Union{     BasisSetData{T, D},      AbstractVector{<:AbstractGTBasisFuncs{T, D}},      Tuple{Vararg{AbstractGTBasisFuncs{T, D}}} } where {T, D}`: The basis set used for the Hartree–Fock approximation.

`nuc::Union{     Tuple{String, Vararg{String, NNMO}} where NNMO,      AbstractVector{String} }`: The nuclei in the studied system.

`nucCoords::Union{AbstractArray{NTuple{D, T}, 1}, Tuple{NTuple{D, T}, Vararg{NTuple{D, T}, NNMO}}, AbstractVector{<:AbstractVector{<:T}}, Tuple{TL, Vararg{TL, NNMO}} where TL<:(AbstractVector{<:T})} where {T, D, NNMO}`: The coordinates of corresponding nuclei.

`config::HFconfig`: The Configuration of selected Hartree–Fock method. For more information  please refer to [`HFconfig`](@ref).

`N::Union{Int, Tuple{Int}, NTuple{2, Int}}`: Total number of electrons, or the number(s) of  electrons with same spin configurations(s). **NOTE:** `N::NTuple{2, Int}` is only supported  by unrestricted Hartree–Fock (UHF).

≡≡≡ Keyword argument(s) ≡≡≡

`printInfo::Bool`: Whether print out the information of iteration steps and result.

`infoLevel::Int`: Printed info's level of details when `printInfo=true`. The higher  (the absolute value of) it is, more intermediate steps will be printed. Once `infoLevel`  achieve `5`, every step will be printed.
