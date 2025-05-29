```
Stats
```

シミュレーションの統計を保持する構造体です。以下のフィールドがあります：

  * `totalSteps::Int`: シミュレーションステップの総数。
  * `simulStepCount::Int`: 同時ステップの数。
  * `evCount::Int`: イベントの数。
  * `numStateSteps::Vector{Int}`: 各状態更新のステップ数を保持するベクター。
  * `numInputSteps::Vector{Int}`: 各入力更新のステップ数を保持するベクター。
