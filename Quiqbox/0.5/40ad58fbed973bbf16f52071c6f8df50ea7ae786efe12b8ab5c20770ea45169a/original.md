```
mul(gf::GaussFunc{T}, coeff::Real; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc

mul(coeff::Real, gf::GaussFunc{T}; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc

mul(gf1::GaussFunc{T}, gf2::GaussFunc{T}; roundAtol::Real=getAtolVal(T)) where {T} -> 
GaussFunc
```

Multiplication between a `Real` number and a [`GaussFunc`](@ref) or two `GaussFunc`s.  `roundAtol` specifies the absolute approximation tolerance of comparing parameters stored  in each `GaussFunc` to determine whether they are treated as "equal"; each parameter in the  returned `GaussFunc` is set to the nearest exact multiple of `0.5atol`. When `roundAtol` is  set to `NaN`, there will be no approximation nor rounding. This function can be called  using `*` syntax with the keyword argument set to it default value. 

**NOTE:** For the `ParamBox` (stored in the input arguments) that are marked as  non-differentiable, they will be fused together if possible to generate new `ParamBox`(s)  no longer linked to the data (input variable) stored in them.

≡≡≡ Example(s) ≡≡≡

```jldoctest; setup = :(push!(LOAD_PATH, "../../src/"); using Quiqbox)
julia> gf1 = GaussFunc(3.0, 1.0)
GaussFunc{Float64, …}{0, 0}[∂∂][{3.0, 1.0}]

julia> gf1 * 2
GaussFunc{Float64, …}{0, 0}[∂∂][{3.0, 2.0}]

julia> gf1 * gf1
GaussFunc{Float64, …}{0, 0}[∂∂][{6.0, 1.0}]

julia> gf1 * 2 * gf1
GaussFunc{Float64, …}{0, 0}[∂∂][{6.0, 2.0}]
```
