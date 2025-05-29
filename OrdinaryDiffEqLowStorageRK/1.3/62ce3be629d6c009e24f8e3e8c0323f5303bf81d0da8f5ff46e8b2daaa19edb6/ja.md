```julia
NDBLSRK144(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
             step_limiter! = OrdinaryDiffEq.trivial_limiter!,
             thread = OrdinaryDiffEq.False(),
             williamson_condition = true)
```

明示的ルンゲ-クッタ法。 14段階、4次低ストレージ法で、輸送支配問題のために最適化された安定領域を持っています。 固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用するべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `williamson_condition`: ブロードキャスト式と関数呼び出し `f` を融合させる最適化を可能にします。ただし、これは `Array` 型にのみ機能します。

## 参考文献

Jens Niegemann, Richard Diehl, Kurt Busch.     効率的な低ストレージルンゲ–クッタスキームと最適化された安定領域。     計算物理学ジャーナル, 231, pp 364-372, 2012.     doi: https://doi.org/10.1016/j.jcp.2011.09.003
