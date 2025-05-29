```
mul(a1::Real, a2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}

mul(a1::CompositeGTBasisFuncs{T, D, <:Any, 1}, a2::Real; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}

mul(a1::CompositeGTBasisFuncs{T, D, <:Any, 1}, 
    a2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    normalizeGTO::Union{Bool, Missing}=missing, 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}
```

Multiplication between two `CompositeGTBasisFuncs{T, D, <:Any, 1}` (e.g.,   [`BasisFunc`](@ref) and [`BasisFuncMix`](@ref)), or a `Real` number and a  `CompositeGTBasisFuncs{T, D, <:Any, 1}`. If `normalizeGTO` is set to `missing` (in  default), The [`GaussFunc`](@ref) inside the output containers will be normalized only if  every input `FloatingGTBasisFuncs` (or inside the input `CompositeGTBasisFuncs`) holds  `hasNormFactor(ai) == true`. `roundAtol` specifies the absolute approximation tolerance of  comparing parameters stored in each `CompositeGTBasisFuncs` to determine whether they are  treated as "equal"; each parameter in the returned `CompositeGTBasisFuncs` is set to the  nearest exact multiple of `0.5atol`. When `roundAtol` is set to `NaN`, there will be no  approximation nor rounding. This function can be called using `*` syntax with the keyword  argument set to it default value.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> bf1 = genBasisFunc([1.0, 1.0, 1.0], ([2.0, 1.0], [0.1, 0.2]));

julia> gaussCoeffOf(bf1)
2×2 Matrix{Float64}:
 2.0  0.1
 1.0  0.2

julia> bf2 = bf1 * 2;

julia> gaussCoeffOf(bf2)
2×2 Matrix{Float64}:
 2.0  0.2
 1.0  0.4

julia> bf3 = bf1 * bf2;

julia> gaussCoeffOf(bf3)
3×2 Matrix{Float64}:
 4.0  0.02
 3.0  0.08
 2.0  0.08
```
