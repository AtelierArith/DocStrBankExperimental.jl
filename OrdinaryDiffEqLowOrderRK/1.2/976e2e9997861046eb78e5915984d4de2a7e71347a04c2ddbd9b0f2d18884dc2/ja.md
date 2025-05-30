```julia
RKM(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。双曲型偏微分方程式の擬似スペクトル離散化に適用したときに良好な安定性特性を持つように設計されたメソッドです。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部ブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{mead1999optimal,   title={Optimal Runge–Kutta methods for first order pseudospectral operators},   author={Mead, JL and Renaut, RA},   journal={Journal of Computational Physics},   volume={152},   number={1},   pages={404–419},   year={1999},   publisher={Elsevier} }
