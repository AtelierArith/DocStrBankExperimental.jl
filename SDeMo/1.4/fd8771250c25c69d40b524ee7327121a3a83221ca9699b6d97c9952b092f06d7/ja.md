```
variableimportance(model, folds, variable; reps=10, optimality=mcc, kwargs...)
```

モデル内の1つの変数の重要性を返します。`samples`キーワードは実行するブートストラップの数を固定します（デフォルトは`10`で、これは不十分です！）。

キーワードは`ConfusionMatrix`に渡されます。
