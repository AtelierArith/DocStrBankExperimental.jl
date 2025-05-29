```
PDEConstrainedFunctionals(objective::Function,constraints::Vector{<:Function},
  state_map::AbstractFEStateMap;analytic_dJ;analytic_dC)
```

`PDEConstrainedFunctionals`のインスタンスを作成します。目的関数と制約の引数は、[`StateParamIntegrandWithMeasure`](@ref)の仕様に従う必要があります。デフォルトでは、目的関数とすべての制約に対して自動微分を使用します。これは、形状導関数をタイプ`Function`として`analytic_dJ`および/または`analytic_dC`のエントリに渡すことで無効にできます。
