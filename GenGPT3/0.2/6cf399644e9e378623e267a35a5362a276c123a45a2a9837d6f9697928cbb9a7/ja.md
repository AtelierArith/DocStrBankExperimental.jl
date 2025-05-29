```
GPT3MixtureTrace
```

言語モデルのプロンプトに対する混合分布によって生成されたトレースです。

`Base.getindex(trace::GPT3MixtureTrace, addr)` は、次の値を `addr` に対してサポートします：

  * `:prompt`: 言語モデルに引数として提供されたプロンプト。
  * `:prior_probs`: 各プロンプトの事前確率。
  * `:post_probs`: 各プロンプトの事後確率。
  * `:joint_probs`: 各プロンプトと出力の同時確率。
  * `:tokens`: 停止シーケンスを含む出力トークンのベクトル。
  * `:output`: 言語モデルによって生成された出力の完了。
  * `:output_scores`: 各プロンプトの下での出力の対数確率。
  * `:score`: プロンプトにわたって周辺化された出力の総対数確率。
