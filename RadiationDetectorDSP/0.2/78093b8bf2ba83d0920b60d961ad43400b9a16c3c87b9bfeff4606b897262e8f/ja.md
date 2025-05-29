```
struct InvSecondOrderCRFilter <: AbstractRadIIRFilter
```

[`SecondOrderCRFilter`](@ref) の逆。提供された時間定数を使用して波形に二重極-零キャンセレーションを適用します。

コンストラクタ:

  * `InvSecondOrderCRFilter(fields...)`

フィールド:

  * `cr::Union{Real, Unitful.AbstractQuantity{<:Real}}`: デコンボルートされる最初の指数の時間定数
  * `cr2::Union{Real, Unitful.AbstractQuantity{<:Real}}`: デコンボルートされる2番目の指数の時間定数
  * `f::Real`: 2番目の指数が寄与する割合ファクター
