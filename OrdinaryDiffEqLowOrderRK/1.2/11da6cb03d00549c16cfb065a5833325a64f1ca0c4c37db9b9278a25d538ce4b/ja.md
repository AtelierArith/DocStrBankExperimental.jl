```julia
SIR54(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。SIR型疫病モデルに適した5次の手法です。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャスティングを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献

@article{Kovalnogov2020RungeKuttaPS,     title={Runge–Kutta pairs suited for SIR‐type epidemic models},     author={Vladislav N. Kovalnogov and Theodore E. Simos and Ch. Tsitouras},     journal={Mathematical Methods in the Applied Sciences},     year={2020},     volume={44},     pages={5210 - 5216}     }
