```julia
SSPRK53_2N1(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
              step_limiter! = OrdinaryDiffEq.trivial_limiter!,
              thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。三次、五段階の明示的強安定性保持（SSP）低ストレージ法。固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されたとき。

## 参考文献

Higueras and T. Roldán.     新しい三次低ストレージSSP明示ルンゲ・クッタ法     arXiv:1809.04807v1.
