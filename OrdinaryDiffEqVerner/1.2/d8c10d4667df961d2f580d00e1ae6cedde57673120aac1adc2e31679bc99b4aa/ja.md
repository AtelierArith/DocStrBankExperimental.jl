```julia
Vern6(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        lazy = true)
```

明示的ルンゲ-クッタ法。ヴァーナーの「最も効率的な」6/5ルンゲ-クッタ法。（遅延6次補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `lazy`: 遅延補間子が使用されるかどうかを決定します。

## 参考文献

@article{verner2010numerically,     title={Numerically optimal Runge–Kutta pairs with interpolants},     author={Verner, James H},     journal={Numerical Algorithms},     volume={53},     number={2-3},     pages={383–396},     year={2010},     publisher={Springer}     }
