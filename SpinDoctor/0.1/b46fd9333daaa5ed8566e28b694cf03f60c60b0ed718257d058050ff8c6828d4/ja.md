```
function solve(
    problem::BTPDE,
    gradient::ScalarGradient,
    odesolver::IntervalConstantSolver;
    callbacks = [],
)
```

Bloch-Torrey偏微分方程を空間でP1有限要素法を用い、時間でθルールを用いて解きます。この時間ステッピングスキームは、暗黙性の度合い`θ`と時間ステップ`Δt`を必要とします：

  * `θ = 0.5`: クランク-ニコルソン（2次）
  * `θ = 1.0`: 暗黙のオイラー（1次）

この関数は区間ごとに定数の`ScalarGradient`にのみ対応しており、それ以外の場合はエラーになります。
