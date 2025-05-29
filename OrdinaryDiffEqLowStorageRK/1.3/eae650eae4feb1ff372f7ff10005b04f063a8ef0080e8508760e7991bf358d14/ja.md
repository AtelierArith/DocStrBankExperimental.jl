```julia
CFRLDDRK64(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
             step_limiter! = OrdinaryDiffEq.trivial_limiter!,
             thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。 低ストレージ法 6段階、4次低ストレージ、低減衰、低分散スキーム。 固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されたとき。

## 参考文献

M. Calvo, J. M. Franco, L. Randez. 計算音響のための新しい最小ストレージルンゲ–クッタスキーム。 計算物理学ジャーナル, 201, pp 1-12, 2004. doi: https://doi.org/10.1016/j.jcp.2004.05.012
