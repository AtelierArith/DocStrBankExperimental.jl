```
genBasisFunc(center::Union{AbstractVector{T}, Tuple{Vararg{T}}, SpatialPoint, Missing}, 
             args..., kws...) where {T<:Union{AbstractFloat, ParamBox}} -> 
Union{FloatingGTBasisFuncs{T}, Vector{<:FloatingGTBasisFuncs{T}}}
```

The constructor of `FloatingGTBasisFuncs`, but it also returns different kinds of  collections (`Vector`) of them based on the input arguments. The first argument `center`  specifies the center coordinate of the generated `FloatingGTBasisFuncs`, and can be left as  `missing` for later assignment.

**NOTE:** Although not marked in the return types, if any allowed input argument can lead  to a `FloatingGTBasisFuncs` with no `GaussFunc` stored inside of it, e.g.,  `genBasisFunc([1.0, 2.0, 3.0], ())`, a `Quiqbox.EmptyBasisFunc` will be generated instead.

≡≡≡ Method 1 ≡≡≡

```
genBasisFunc(center, GsOrCoeffs, Ls; normalizeGTO=false) -> 
FloatingGTBasisFuncs
```

=== Positional argument(s) ===

`GsOrCoeffs::Union{     AbstractGaussFunc{T1},      AbstractVector{<:AbstractGaussFunc{T1}},      Tuple{Vararg{AbstractGaussFunc{T1}}},      NTuple{2, Union{T1, Array{T1, 0}, ParamBox{T1}},      NTuple{2, AbstractVector{<:Union{T1, Array{T1, 0}, ParamBox{T1}}}} } where {T1<:AbstractFloat}`: A collection of concentric `GaussFunc` that will be used to  construct the basis function. To simplify the procedure, it can also be in the form of a  `NTuple{2}` of the exponent coefficient(s)`::Union{AbstractFloat,  AbstractVector{<:AbstractFloat}}` and contraction coefficients`::Union{AbstractFloat,  AbstractVector{<:AbstractFloat}}` of the [`GaussFunc`](@ref)(s) to be input.

`Ls::Union{     T2,      AbstractVector{T2},      NTuple{<:Any, T2} } where {T2<:Union{NTuple{D, Int}, LTuple{D}} where {D}}`: A collection of at least one  angular momentum configuration within the same subshell, in the Cartesian coordinate  representation. E.g., for p shell it can be set to `((1,0,0), (0,1,0))`. This will  determine the number of spatial orbitals and their angular momentum respectively to be  stored in the output `FloatingGTBasisFuncs`.

=== Keyword argument(s) ===

`normalizeGTO::Bool`: Determine whether the inside `GaussFunc`(s) will be normalized in the  during the calculation. 

=== Example(s) ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], GaussFunc(2., 1.), (0, 1, 0))
BasisFunc{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][X⁰Y¹Z⁰]
```

≡≡≡ Method 2 ≡≡≡

```
genBasisFunc(center, GsOrCoeffs, subshell="s"; normalizeGTO=false) -> 
FloatingGTBasisFuncs

genBasisFunc(center, GsOrCoeffs, subshell, lFilter; normalizeGTO=false) -> 
FloatingGTBasisFuncs
```

=== Positional argument(s) ===

`subshell::Union{String, Symbol}`: The third argument of the constructor can also be the  name of a subshell, which will make sure the output is a `BasisFuncs` that contains the  spatial orbitals that fully occupy the subshell.

`lFilter::Tuple{Vararg{Bool}}`: When this 4th argument is provided, it can determine the  orbital(s) to be included based on the given `subshell`. The order of the corresponding  orbital angular momentum(s) can be inspected using function `orbitalLin`.

=== Keyword argument(s) ===

`normalizeGTO::Bool`: Same as the one defined in method 1.

=== Example(s) ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], (2., 1.), "p")
BasisFuncs{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][3/3]

julia> genBasisFunc([0.,0.,0.], (2., 1.5), "p", (true, false, true))
BasisFuncs{Float64, 3, 1, 1, …}{0, 0, 0}[(0.0, 0.0, 0.0)][2/3]
```

≡≡≡ Method 3 ≡≡≡

```
genBasisFunc(center, BSkey, atm="H"; unlinkCenter=false) -> 
Vector{<:FloatingGTBasisFuncs}
```

=== Positional argument(s) ===

`BSkey::String`: The name of an existed atomic basis set. The supported options are in  `["STO-2G", "STO-3G", "STO-6G", "3-21G", "6-31G", "cc-pVDZ", "cc-pVTZ", "cc-pVQZ"]`.

`atm::Union{String, Symbol}`: The name of the atom corresponding to the chosen basis set.  The supported options are in `["H", "He", "Li", "Be", "B", "C", "N", "O", "F", "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca"]`.

=== Keyword argument(s) ===

`unlinkCenter::Bool`: Determine whether the centers of constructed `FloatingGTBasisFuncs`  are linked to each other. If set to `true`, the center of each `FloatingGTBasisFuncs` is a  `Base.deepcopy` of each other. Otherwise, they share the same underlying data so changing  the value of one will affect others.

=== Example(s) ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> genBasisFunc([0.,0.,0.], "6-31G");

julia> genBasisFunc([0.,0.,0.], "STO-3G", "Li");
```

≡≡≡ Method 4 ≡≡≡

```
genBasisFunc(b::FloatingGTBasisFuncs{T, D}, newFieldVal) where {T, D} -> 
FloatingGTBasisFuncs{T, D}
```

=== Positional argument(s) ===

`newFieldVal::Union{     SpatialPoint{T, D},      Tuple{AbstractGaussFunc{T}, Vararg{AbstractGaussFunc{T}}},      Tuple{LTuple{D, 𝑙}, Vararg{LTuple{D, 𝑙}}} where 𝑙,      Bool } where {T<:AbstractFloat, D}`: Any one of the fields inside a `FloatingGTBasisFuncs`  except `param`.

This method outputs a `FloatingGTBasisFuncs` that has identical fields as the input one  except the field that can be replaced by `newFieldVal` (and `param` if the replaced field  contains [`ParamBox`](@ref)).

=== Example(s) ===

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> bf1 = genBasisFunc([1., 2., 3.], (2.0, 1.0), (0, 0, 0));

julia> bf2 = genBasisFunc([1., 2., 3.], (2.0, fill(1.0)), (0, 0, 1));

julia> bf1 = genBasisFunc(bf1, bf2.l);

julia> hasEqual(bf1, bf2)
true
```
