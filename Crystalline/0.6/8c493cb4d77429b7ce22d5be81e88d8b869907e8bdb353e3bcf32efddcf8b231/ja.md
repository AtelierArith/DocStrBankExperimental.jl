```julia
cosets(
    g::Crystalline.SiteGroup
) -> Array{Crystalline.SymOperation{D}, 1} where D

```

`SiteGroup` `g` の左コセット代表を返します（その親空間群内で）。

コセットは、ワイコフ位置 [`position(g)`](@ref) の軌道を生成し（[`orbit(::SiteGroup)`](@ref) も参照）、`g` 自体の操作と共に基礎となる空間群の左コセット分解を提供します。

[`cosets(::AbstractVector, ::AbstractVector)`](@ref) も参照してください。このメソッドは、`cosets(spacegroup(sgnum), g)` に対して同等ですが、一般的には異なる代表を返す場合があります。
