```julia
CKLLSRK75_4M_5R(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                  step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                  thread = OrdinaryDiffEq.False())
```

明示的ルンゲ・クッタ法。 CKLLSRK75*4M*5R: 7段階の低ストレージ法、5次の低ストレージスキームで、圧縮可能なナビエ–ストークス方程式に最適化されています。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャストが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{kennedy2000low, title={Low-storage, explicit Runge–Kutta schemes for the compressible Navier–Stokes equations}, author={Kennedy, Christopher A and Carpenter, Mark H and Lewis, R Michael}, journal={Applied numerical mathematics}, volume={35}, number={3}, pages={177–219}, year={2000}, publisher={Elsevier}}
