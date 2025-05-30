```julia
RKO65(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。5次の方法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列で行われるべきか（`thread = OrdinaryDiffEq.False()`）または複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Tsitouras, Ch. "Explicit Runge–Kutta methods for starting integration of     Lane–Emden problem." Applied Mathematics and Computation 354 (2019): 353-364.     doi: https://doi.org/10.1016/j.amc.2019.02.047
