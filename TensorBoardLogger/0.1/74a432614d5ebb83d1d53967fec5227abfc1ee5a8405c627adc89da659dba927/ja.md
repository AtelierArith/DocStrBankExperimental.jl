```
set_step_increment!(lg, increment) -> Int
```

ロガー `lg` のイテレーションカウンタに対して、ログが行われるたびに適用されるデフォルトのインクリメントを設定します。

ログを行う際に `log_step_increment=some_increment` を渡すことで上書きすることができます。
