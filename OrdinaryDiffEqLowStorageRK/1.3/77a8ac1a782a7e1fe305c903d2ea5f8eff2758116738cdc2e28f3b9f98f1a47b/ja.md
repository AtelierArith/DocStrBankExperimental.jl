```julia
TSLDDRK74(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。 低ストレージ法 7段階、4次低ストレージ低減衰、低分散スキームで、最大の精度と安定性限界を虚数軸に沿って持つ。 固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

Kostas Tselios, T. E. Simos. 最小分散と減衰を持つ最適化ルンゲ–クッタ法。計算音響学から生じる問題に対して。Physics Letters A, 393(1-2), pp 38-47, 2007. doi: https://doi.org/10.1016/j.physleta.2006.10.072
