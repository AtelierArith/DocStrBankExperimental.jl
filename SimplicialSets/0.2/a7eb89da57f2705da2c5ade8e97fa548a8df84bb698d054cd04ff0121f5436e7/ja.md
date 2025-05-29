```
opposite(x::T) where T <: AbstractSimplex -> OppositeSimplex
opposite(x::T) where {S, T <: OppositeSimplex{S}} -> S
opposite(x::T) where T <: ProductSimplex -> ProductSimplex
```

`x`の反対単体の「解釈されたバージョン」を返します：

  * `x`がすでに`OppositeSimplex`である場合、基礎となる単体を返します。
  * `x`が`ProductSimplex`である場合、コンポーネントに`opposite`を適用し、対応する`ProductSimplex`を返します。
  * その他のすべての場合、`OppositeSimplex(x)`を返します。

[`OppositeSimplex`](@ref)、[`opposite(::AbstractTensor)`](@ref)、[`opposite(::AbstractLinear)`](@ref)も参照してください。
