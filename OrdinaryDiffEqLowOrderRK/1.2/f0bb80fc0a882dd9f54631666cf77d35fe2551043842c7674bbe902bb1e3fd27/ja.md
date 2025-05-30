```julia
DP5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。ドーマンド-プリンスの5/4ルンゲ-クッタ法。（自由な4次補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 内部のブロードキャスティングが適切なCPU配列で直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{dormand1980family,     title={A family of embedded Runge-Kutta formulae},     author={Dormand, John R and Prince, Peter J},     journal={Journal of computational and applied mathematics},     volume={6},     number={1},     pages={19–26},     year={1980},     publisher={Elsevier}     }
