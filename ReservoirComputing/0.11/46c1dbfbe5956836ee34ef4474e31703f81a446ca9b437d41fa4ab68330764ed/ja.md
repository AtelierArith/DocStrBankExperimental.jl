```
RNN(活性化関数, 漏れ係数)
RNN(;活性化関数=tanh, 漏れ係数=1.0)
```

エコー状態ネットワーク（`ESN`）のための再帰神経ネットワーク（RNN）初期化子を返します。

# 引数

  * `活性化関数`: RNNで使用される活性化関数。
  * `漏れ係数`: RNNで使用される漏れ係数。

# キーワード引数

  * `活性化関数`: RNNで使用される活性化関数。デフォルトは`tanh_fast`。
  * `漏れ係数`: RNNで使用される漏れ係数。デフォルトは1.0。
