```
presmoothing(F::NEAT, LogLinearFormula(df::Int64), LogLinearFormula(df::Int64))
```

スムーズ化された頻度テーブルを `SmoothedNEATFreqTab` と `glm` フィッティングオブジェクトとして返しますが、返される `interval` と `marginal` 要素はスムーズ化されたスコアに基づいていません。

元の頻度データの最初の C モーメントを保持するために、`LogLinearFormula(C)` を `fml` に渡しました。C は自由度です。
