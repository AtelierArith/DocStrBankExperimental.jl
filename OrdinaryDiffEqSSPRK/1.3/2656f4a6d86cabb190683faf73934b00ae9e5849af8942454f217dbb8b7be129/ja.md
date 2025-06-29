```julia
KYK2014DGSSPRK_3S2(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                     step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                     thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。 不連続ガレルキン法のための最適な強安定性保持ルンゲ-クッタ時間離散化

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されたとき。

## 参考文献

@article{kubatko2014optimal, title={Optimal strong-stability-preserving Runge–Kutta time discretizations for discontinuous Galerkin methods}, author={Kubatko, Ethan J and Yeager, Benjamin A and Ketcheson, David I}, journal={Journal of Scientific Computing}, volume={60}, pages={313–344}, year={2014}, publisher={Springer}}
