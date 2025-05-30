```julia
SSPRK432(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。3次、4段階の明示的強安定性保持（SSP）法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Gottlieb, Sigal, David I. Ketcheson, and Chi-Wang Shu.     強安定性保持ルンゲ・クッタ法と多段時間離散化。     World Scientific, 2011.     例6.1
