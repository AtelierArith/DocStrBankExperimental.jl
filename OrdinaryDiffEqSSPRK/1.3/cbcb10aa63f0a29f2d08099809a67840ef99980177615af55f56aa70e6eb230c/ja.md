```julia
SSPRK33(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。第三次、三段階の明示的強安定性保持（SSP）法。固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Shu, Chi-Wang, and Stanley Osher.     効率的な本質的非振動的衝撃捕捉スキームの実装。     Computational Physicsジャーナル 77.2 (1988): 439-471.     https://doi.org/10.1016/0021-9991(88)90177-5
