```
estimate_value(estimator, mdp, state, remaining_depth)
```

値の推定を返します。

`remaining_depth` 引数は、`estimate_value` が呼び出されるポイントから MCTS ソルバーの `depth` 引数までの残りのステップ数を示します。安全に無視できますが、*ルートノード*から固定のホライズンにロールアウトを制限するために使用できます。
