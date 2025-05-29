```
NormedCartesianSpace{T<:Union{BanachSpace,Tuple{Vararg{BanachSpace}}},S<:BanachSpace} <: BanachSpace
```

Cartesian Banach space.

Fields:

  * `inner :: T`
  * `outer :: S`

See also: [`Ell1`](@ref), [`Ell2`](@ref) and [`EllInf`](@ref).

# Examples

```jldoctest
julia> NormedCartesianSpace(Ell1(), EllInf())
NormedCartesianSpace(ℓ¹(), ℓ∞())

julia> NormedCartesianSpace((Ell1(), Ell2()), EllInf())
NormedCartesianSpace((ℓ¹(), ℓ²()), ℓ∞())
```
