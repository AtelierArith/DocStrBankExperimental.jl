```
struct SecondOrderCRFilter <: AbstractRadIIRFilter
```

二次CRハイパスフィルタ。フィルタには逆[`InvSecondOrderCRFilter`](@ref)があります。

コンストラクタ:

  * `SecondOrderCRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: デコンボルブされる最初の指数の時間定数
  * `cr2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: デコンボルブされる二番目の指数の時間定数
  * `f::Real`: 二番目の指数が寄与する割合ファクタ
