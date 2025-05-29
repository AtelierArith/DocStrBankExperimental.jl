```
SetOpportunisticEvaluation(p::DSProblem; opportunistic::Bool=true)
```

機会評価を設定/解除します（デフォルトで有効）。

機会評価を使用する場合、改善されたコストを持つ最初の許可された評価点が新しい現行解として設定されます。進行中のバリア制約を使用している場合、この点は実現不可能な場合があります。
