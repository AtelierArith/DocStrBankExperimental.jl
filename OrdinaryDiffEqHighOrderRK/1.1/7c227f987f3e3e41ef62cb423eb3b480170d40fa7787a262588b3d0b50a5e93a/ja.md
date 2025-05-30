```julia
PFRK87(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False(),
         omega = 0.0)
```

明示的ルンゲ-クッタ法。位相適合ルンゲ-クッタ法の8次。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用すべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `omega`: 周期的な位相推定。正確な場合、この方法は数値的な消散をゼロにします。

## 参考文献
