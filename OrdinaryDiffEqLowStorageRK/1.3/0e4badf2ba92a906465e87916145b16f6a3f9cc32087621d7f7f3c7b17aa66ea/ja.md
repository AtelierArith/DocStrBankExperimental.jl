```julia
CarpenterKennedy2N54(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
                       step_limiter! = OrdinaryDiffEq.trivial_limiter!,
                       thread = OrdinaryDiffEq.False(),
                       williamson_condition = true)
```

明示的ルンゲ-クッタ法。カルパンターとケネディによる4次、5段階の低ストレージ法（自由な3次のエルミート補間子）。固定タイムステップのみ。双曲型PDE（安定性特性）用に設計されています。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されたとき。
  * `williamson_condition`: ブロードキャスト式と関数呼び出し `f` を融合させる最適化を可能にします。ただし、`Array` 型にのみ機能します。

## 参考文献

@article{carpenter1994fourth,     title={Fourth-order 2N-storage Runge-Kutta schemes},     author={Carpenter, Mark H and Kennedy, Christopher A},     year={1994}     }
