```julia
struct UnconstrainedObjective{D<:Cthonios.Domain, I<:Cthonios.AbstractIntegral, T} <: Cthonios.AbstractObjective
```

  * `domain::Cthonios.Domain`
  * `integral::Cthonios.AbstractIntegral`
  * `timer::Any`

目的関数を評価するためのオブジェクトタイプ。関数は目的関数、その勾配、およびヘッセ行列のそれぞれの数値評価に対応しています。 `domain` - ドメインオブジェクト  `integral` - AbstractIntegral  `timer` - すでにセットアップされたタイマー。
