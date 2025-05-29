```
EllInf{T<:Union{Weight,Tuple{Vararg{Weight}}}} <: BanachSpace
```

Weighted $\ell^\infty$ space.

Field:

  * `weight :: T`

Constructors:

  * `EllInf(::Weight)`
  * `EllInf(::Tuple{Vararg{Weight}})`
  * `EllInf()`: equivalent to `EllInf(IdentityWeight())`
  * `EllInf(weight::Weight...)`: equivalent to `EllInf(weight)`

Unicode alias [`ℓ∞`](@ref) can be typed by `\ell<tab>\infty<tab>` in the Julia REPL and in many editors.

See also: [`Ell1`](@ref) and [`Ell2`](@ref).

# Examples

```jldoctest
julia> EllInf()
ℓ∞()

julia> EllInf(GeometricWeight(1.0))
ℓ∞(GeometricWeight(1.0))

julia> EllInf(GeometricWeight(1.0), AlgebraicWeight(2.0))
ℓ∞(GeometricWeight(1.0), AlgebraicWeight(2.0))
```
