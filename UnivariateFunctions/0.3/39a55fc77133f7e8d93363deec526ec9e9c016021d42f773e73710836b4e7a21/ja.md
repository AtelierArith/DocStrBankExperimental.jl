```
evaluate(f::UnivariateFunction, r::Real)
evaluate(f::UnivariateFunction, d::Union{Date,DateTime})
evaluate(f::UnivariateFunction, x::DatePeriod)
```

これは、要求された点で関数を評価します。`Date`または`DateTime`が入力されると、最初に`years_from_global_base`関数を使用してスカラーに変換されます。`DatePeriod`は`period_length`関数を使用して変換されます。
