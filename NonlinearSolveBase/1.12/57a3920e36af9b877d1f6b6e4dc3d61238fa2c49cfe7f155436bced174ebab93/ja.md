```
NonlinearSolveBase.RelNormSafeTerminationMode <: NonlinearSolveBase.AbstractSafeNonlinearTerminationMode
```

本質的には [`RelNormTerminationMode`](@ref) + 最後の `patience_steps` で改善がなかった場合に終了 + 解が爆発する（発散する）場合に終了します。

## コンストラクタ

```
NonlinearSolveBase.RelNormSafeTerminationMode(
    internalnorm; protective_threshold = nothing,
    patience_steps = 100, patience_objective_multiplier = 3,
    min_max_factor = 1.3, max_stalled_steps = nothing
)
```

ここで `internalnorm` は終了条件に使用するノルムです。`norm(_, 2)`, `norm`, `norm(_, Inf)`, および `maximum(abs, _)` に対して特別な処理が行われます。
