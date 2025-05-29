```julia
BS3(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
      step_limiter! = OrdinaryDiffEq.trivial_limiter!,
      thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。ボガッキとシャンピンの埋め込み誤差推定器を持つ三次、四段階のFSAL法。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{bogacki19893,     title={A 3 (2) pair of Runge-Kutta formulas},     author={Bogacki, Przemyslaw and Shampine, Lawrence F},     journal={Applied Mathematics Letters},     volume={2},     number={4},     pages={321–325},     year={1989},     publisher={Elsevier}     }
