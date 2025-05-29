```
DiscreteEvolve(numTraits::Int64, tree::BinaryTree)
```

バイナリツリー `tree` に沿って離散的なスイッチング特性を進化させる関数です。スイッチする特性の数 `numTraits` と特性間でスイッチするレート `switch_rate`（デフォルト値は0.5）を受け取ります。
