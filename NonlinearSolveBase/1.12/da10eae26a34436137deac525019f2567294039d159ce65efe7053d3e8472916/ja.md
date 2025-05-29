```
NonlinearSolveBase.RelNormSafeBestTerminationMode <: NonlinearSolveBase.AbstractSafeBestNonlinearTerminationMode
```

本質的には [`RelNormSafeTerminationMode`](@ref) ですが、これまでに見つかった最良の解をキャッシュします。

## コンストラクタ

```
NonlinearSolveBase.RelNormSafeBestTerminationMode(
    internalnorm; protective_threshold = nothing,
    patience_steps = 100, patience_objective_multiplier = 3,
    min_max_factor = 1.3, max_stalled_steps = nothing
)
```

ここで `internalnorm` は終了条件に使用するノルムです。`norm(_, 2)`、`norm`、`norm(_, Inf)`、および `maximum(abs, _)` に対して特別な処理が行われます。
