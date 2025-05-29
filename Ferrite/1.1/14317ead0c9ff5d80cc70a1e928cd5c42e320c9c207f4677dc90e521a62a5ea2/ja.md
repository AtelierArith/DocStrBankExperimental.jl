```
update!(ch::ConstraintHandler, time::Real=0.0)
```

新しい時間に対して時間依存の不均一性を更新します。これは、適用可能な場合に `f(x)` または `f(x, t)` を呼び出し、`f` はハンドラー内の制約に対応する関数で、不均一性を計算します。

これは `close!(::ConstraintHandler)` で暗黙的に呼び出されることに注意してください。
