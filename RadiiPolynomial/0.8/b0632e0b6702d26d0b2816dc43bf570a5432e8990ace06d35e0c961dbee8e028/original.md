```
Ell1{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

Weighted $\ell^1$ space.

Field:

  * `weight :: T`

Constructors:

  * `Ell1(::Weight)`
  * `Ell1(::Tuple{Vararg{Weight}})`
  * `Ell1()`: equivalent to `Ell1(IdentityWeight())`
  * `Ell1(weight::Weight...)`: equivalent to `Ell1(weight)`

Unicode alias [`ℓ¹`](@ref) can be typed by `\ell<tab>\^1<tab>` in the Julia REPL and in many editors.

See also: [`Ell2`](@ref) and [`EllInf`](@ref).

# Examples

```jldoctest
julia> Ell1()
ℓ¹()

julia> Ell1(GeometricWeight(1.0))
ℓ¹(GeometricWeight(1.0))

julia> Ell1(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ¹(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
