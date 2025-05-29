```
direct_to_explicit(ps::AbstractRENParams{T}, return_h=false) where T
```

RENの直接パラメータ化を明示的パラメータ化に変換します。

`ps`にエンコードされたパラメータ化を使用して、ユーザー定義の行動制約のセットを自然に満たす[`ExplicitRENParams`](@ref)オブジェクトを構築します。

# 引数

  * `ps::AbstractRENParams`: RENの明示的パラメータ化に変換するための行動制約を持つ直接パラメータ化（例: [`GeneralRENParams`](@ref)）。
  * `return_h::Bool=false`: H行列を直接返すかどうか（[Revay et al. (2021)](https://arxiv.org/abs/2104.05942)を参照）。デバッグやモデル分析に便利です。`false`の場合、関数は`ExplicitRENParams{T}`型のオブジェクトを返します。

他に[`GeneralRENParams`](@ref)、[`ContractingRENParams`](@ref)、[`LipschitzRENParams`](@ref)、[`PassiveRENParams`](@ref)も参照してください。
