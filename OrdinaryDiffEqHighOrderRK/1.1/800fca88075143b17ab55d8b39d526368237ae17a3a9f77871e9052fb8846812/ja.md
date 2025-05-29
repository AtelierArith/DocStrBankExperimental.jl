```julia
TsitPap8(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
           step_limiter! = OrdinaryDiffEq.trivial_limiter!,
           thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。 Tsitouras-Papakostas 8/7 ルンゲ-クッタ法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献
