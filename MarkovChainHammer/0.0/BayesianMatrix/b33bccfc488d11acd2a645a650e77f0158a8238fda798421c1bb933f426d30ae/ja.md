```
uninformative_prior(number_of_states; scale=eps(1e2))
```

ベイジアンジェネレーターオブジェクトのための非情報的事前分布を構築します。

# 引数

  * `number_of_states::Int`: ベイジアンジェネレーターオブジェクトの状態数。

# キーワード引数

  * `scale::Number=eps(1e2)`: ガンマ分布とディリクレ分布のスケールパラメータ。

# 戻り値

  * `GeneratorParameterDistributions`: ベイジアンジェネレーターオブジェクトのための非情報的事前分布。
