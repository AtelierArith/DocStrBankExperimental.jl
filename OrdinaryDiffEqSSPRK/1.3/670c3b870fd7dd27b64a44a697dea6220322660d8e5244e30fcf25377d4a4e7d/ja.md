```julia
SSPRK932(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。第三次、九段階の明示的強安定性保持（SSP）法。

代わりに `SSPRK43` を使用することを検討してください。これは同じ主な方法と改良された埋め込み法を使用します。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Gottlieb, Sigal, David I. Ketcheson, and Chi-Wang Shu.     強安定性保持ルンゲ・クッタ法と多段階時間離散化。     World Scientific, 2011.
