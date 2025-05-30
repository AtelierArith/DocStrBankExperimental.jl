```julia
TanYam7(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
          step_limiter! = OrdinaryDiffEq.trivial_limiter!,
          thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。田中-山下7ルンゲ-クッタ法。（7次の補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

田中 M., 村松 S., 山下 S., (1992), いくつかの9段階7次ルンゲ-クッタ法の最適化について, 日本情報処理学会, 33 (12), pp. 1512-1526.
