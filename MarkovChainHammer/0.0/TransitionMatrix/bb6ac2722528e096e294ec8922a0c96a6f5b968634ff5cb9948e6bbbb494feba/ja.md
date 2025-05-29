sparse*perron*frobenius(markov_chain; step = 1)

# 説明

```
スパース形式のマルコフ連鎖からペロン・フロベニウス行列を計算します
```

# 引数

  * `markov_chain::AbstractVector`: 各時間ステップにおけるマルコフ連鎖の状態を表す整数のベクトル。

# キーワード引数

  * `step::Integer=1`: 構築された演算子のステップサイズ。

# 戻り値

  * `perron_frobenius_matrix::Matrix`: スパース形式のマルコフ連鎖のペロン・フロベニウス行列。
