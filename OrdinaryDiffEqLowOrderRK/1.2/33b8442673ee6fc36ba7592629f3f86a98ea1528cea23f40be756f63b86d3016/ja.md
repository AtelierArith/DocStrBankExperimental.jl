```julia
BS5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False(),
      lazy = true)
```

明示的ルンゲ-クッタ法。ボガッキ-シャンピン 5/4 ルンゲ-クッタ法。（遅延 5 次補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切な CPU 配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Julia が複数のスレッドで起動されるとき。
  * `lazy`: 遅延補間子が使用されるかどうかを決定します。

## 参考文献

@article{bogacki1996efficient,     title={An efficient runge-kutta (4, 5) pair},     author={Bogacki, P and Shampine, Lawrence F},     journal={Computers \& Mathematics with Applications},     volume={32},     number={6},     pages={15–28},     year={1996},     publisher={Elsevier}     }
