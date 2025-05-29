```
Ell2{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

Weighted $\ell^2$ space.

Field:

  * `weight :: T`

Constructors:

  * `Ell2(::Weight)`
  * `Ell2(::Tuple{Vararg{Weight}})`
  * `Ell2()`: equivalent to `Ell2(IdentityWeight())`
  * `Ell2(weight::Weight...)`: equivalent to `Ell2(weight)`

Unicode alias [`ℓ²`](@ref) can be typed by `\ell<tab>\^2<tab>` in the Julia REPL and in many editors.

See also: [`Ell1`](@ref) and [`EllInf`](@ref).

# Examples

```jldoctest
julia> Ell2()
ℓ²()

julia> Ell2(BesselWeight(1.0))
ℓ²(BesselWeight(1.0))

julia> Ell2(BesselWeight(1.0), GeometricWeight(2.0))
ℓ²(BesselWeight(1.0), GeometricWeight(2.0))
```
