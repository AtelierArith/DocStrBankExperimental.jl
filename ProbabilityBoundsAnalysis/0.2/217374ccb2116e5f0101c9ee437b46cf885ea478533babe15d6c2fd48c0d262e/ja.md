```
mutable struct pbox <: AbstractPbox
```

確率境界分析で使用される基本型。上限（u）と下限（d/down）cdf、平均と分散の区間境界、分布の形状（例：正規分布）によって定義される確率分布のセット。

部分的な情報が与えられた場合（例：モーメントに関する境界がない場合）、他の特性は提供された情報から決定されます。

# コンストラクタ

  * `pbox()                     => 空のケース`
  * `pbox(u :: Real)            => スカラーケース`
  * `pbox(u :: Real, d :: Real) => 区間ケース`
  * `pbox(u :: Array{<:Real}, d :: Array{<:Real}, shape :: String, ml :: Real, mh :: Real, vl :: Real, vh :: Real)`

ここで、ml/mhは下限/上限の平均、vl/vhは下限/上限の分散です。

参照：[`mean`](@ref)、[`var`](@ref)、[`uniform`](@ref)、[`normal`](@ref)、[`conv`](@ref)、[`copula`](@ref)
