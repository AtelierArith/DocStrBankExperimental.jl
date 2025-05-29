```
add(b1::CompositeGTBasisFuncs{T, D, <:Any, 1}, 
    b2::CompositeGTBasisFuncs{T, D, <:Any, 1}; 
    roundAtol::Real=getAtolVal(T)) where {T, D} -> 
CompositeGTBasisFuncs{T, D, <:Any, 1}
```

Addition between two `CompositeGTBasisFuncs{T, D, <:Any, 1}` such as [`BasisFunc`](@ref)  and [`BasisFuncMix`](@ref). `roundAtol` specifies the absolute approximation tolerance of  comparing parameters stored in each `CompositeGTBasisFuncs` to determine whether they are  treated as "equal"; each parameter in the returned `CompositeGTBasisFuncs` is set to the  nearest exact multiple of `0.5atol`. When `roundAtol` is set to `NaN`, there will be no  approximation nor rounding. This function can be called using `+` syntax with the keyword  argument set to it default value. 

**NOTE:** For the `ParamBox` (stored in the input  arguments) that are marked as non-differentiable, they will be fused together if possible  to generate new `ParamBox`(s) no longer linked to the input variable stored in them.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> bf1 = genBasisFunc([1.,1.,1.], (2.,1.));

julia> bf2 = genBasisFunc([1.,1.,1.], (2.,2.));

julia> bf3 = bf1 + bf2;

julia> bf3.gauss[1].con() == bf1.gauss[1].con() + bf2.gauss[1].con()
true
```
