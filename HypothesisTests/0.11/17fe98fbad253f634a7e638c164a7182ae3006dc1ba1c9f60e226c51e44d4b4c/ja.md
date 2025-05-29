```
ClarkWestTest(e1::AbstractVector{<:Real}, e2::AbstractVector{<:Real}, lookahead::Integer=1)
```

2つのネストされた予測モデルのパフォーマンスが等しいかどうかを、サンプル外の平均二乗予測誤差の観点から検定します。

`e1`は小さい（ネストされた）モデルからの予測のベクトルであり、`e2`は大きいモデルからの予測誤差のベクトルで、`lookahead`は予測のステップ数です。通常、帰無仮説は2つのモデルが同等に良いパフォーマンスを示すこと（両側検定）ですが、時には大きいモデルがより良いパフォーマンスを示すかどうかを検定します。これは、例えば5%の有意水準（右尾検定）で1.645を超える正の検定統計量によって示されます。

実装: [`pvalue`](@ref)

# 参考文献

  * Clark, T. E., West, K. D. 2006, Using out-of-sample mean squared prediction errors to test the martingale difference hypothesis. Journal of Econometrics, 135(1): 155–186.
  * Clark, T. E., West, K. D. 2007, Approximately normal tests for equal predictive accuracy in nested models. Journal of Econometrics, 138(1): 291–311.
