```
StopWhenStepsizeLess <: StoppingCriterion
```

は、最後の反復中に決定または見つかった最後のステップサイズを見て停止するための閾値を保存します [`AbstractManoptSolverState`](@ref) から。

# コンストラクタ

```
StopWhenStepsizeLess(ε)
```

停止基準を閾値 `ε` に初期化します。
