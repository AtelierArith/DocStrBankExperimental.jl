```julia
Anas5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
        step_limiter! = OrdinaryDiffEq.trivial_limiter!,
        thread = OrdinaryDiffEq.False(),
        w = 1)
```

明示的ルンゲ-クッタ法。周期的問題のために設計された4次のルンゲ-クッタ法です。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `w`: 周期性の推定値で、正確な場合、この方法は5次になります

（そうでない場合は、より良い推定のために誤差が少ない4次になります）。

## 参考文献

@article{anastassi2005optimized, title={An optimized Runge–Kutta method for the solution of orbital problems}, author={Anastassi, ZA and Simos, TE}, journal={Journal of Computational and Applied Mathematics}, volume={175}, number={1}, pages={1–9}, year={2005}, publisher={Elsevier}}
