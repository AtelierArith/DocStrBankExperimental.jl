```julia
CKLLSRK54_3M_4R(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                  step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                  thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。圧縮性ナビエ–ストークス方程式に最適化された5段階の低ストレージ法、4次低ストレージスキーム。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、または複数のスレッドを使用するべきかを決定します（`thread = OrdinaryDiffEq.True()`）。

## 参考文献

@article{kennedy2000low, title={Low-storage, explicit Runge–Kutta schemes for the compressible Navier–Stokes equations}, author={Kennedy, Christopher A and Carpenter, Mark H and Lewis, R Michael}, journal={Applied numerical mathematics}, volume={35}, number={3}, pages={177–219}, year={2000}, publisher={Elsevier}}
