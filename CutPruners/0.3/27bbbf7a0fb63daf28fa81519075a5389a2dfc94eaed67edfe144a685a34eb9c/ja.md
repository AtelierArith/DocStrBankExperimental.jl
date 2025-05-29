```
DecayCutPruningAlgo <: AbstractCutPruningAlgo
```

信頼度が初めて `newcuttrust + bonus` であり、最適化が行われるたびに `trust -> λ * trust + used` を使用して更新される場合、信頼度が低いカットを削除します。値 `used` は、カットが使用された場合は 1、そうでない場合は 0 です。このカットがこのカットを使用して問題によって与えられた試行を使用して生成された場合、`mycutbonus` に等しいボーナスがあります。カットの双対値がゼロでない場合、そのカットは使用されたと言います。
