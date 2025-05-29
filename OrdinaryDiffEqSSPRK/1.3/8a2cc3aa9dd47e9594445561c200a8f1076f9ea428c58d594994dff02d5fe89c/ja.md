```julia
SSPRKMSVS32(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
              step_limiter! = OrdinaryDiffEq.trivial_limiter!,
              thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。第二次、三段階の明示的強安定性保持（SSP）線形多段階法。この方法には誤差推定器が付属しておらず、固定の時間ステップサイズが必要です。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Shu, Chi-Wang.     総変動減少時間離散化。     SIAM Journal on Scientific and Statistical Computing 9, no. 6 (1988): 1073-1084.     [DOI: 10.1137/0909073](https://doi.org/10.1137/0909073)
