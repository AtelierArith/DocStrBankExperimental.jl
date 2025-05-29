```
ノルム付きカルテジアン空間{T<:Union{バナッハ空間,タプル{Vararg{バナッハ空間}}},S<:バナッハ空間} <: バナッハ空間
```

カルテジアンバナッハ空間。

フィールド:

  * `inner :: T`
  * `outer :: S`

参照: [`Ell1`](@ref), [`Ell2`](@ref) および [`EllInf`](@ref)。

# 例

```jldoctest
julia> NormedCartesianSpace(Ell1(), EllInf())
NormedCartesianSpace(ℓ¹(), ℓ∞())

julia> NormedCartesianSpace((Ell1(), Ell2()), EllInf())
NormedCartesianSpace((ℓ¹(), ℓ²()), ℓ∞())
```
