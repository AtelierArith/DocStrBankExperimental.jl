```julia
ORK256(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
         step_limiter! = OrdinaryDiffEq.trivial_limiter!,
         thread = OrdinaryDiffEq.False(),
         williamson_condition = true)
```

明示的ルンゲ・クッタ法。波動伝播方程式のための2次、5段階の手法。固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されたとき。
  * `williamson_condition`: ブロードキャスト式を関数呼び出し `f` と融合させる最適化を可能にします。ただし、`Array` 型にのみ機能します。

## 参考文献

Matteo Bernardini, Sergio Pirozzoli.     波動伝播現象のためのルンゲ・クッタスキームの最適化に関する一般的戦略。     計算物理学ジャーナル, 228(11), pp 4182-4199, 2009.     doi: https://doi.org/10.1016/j.jcp.2009.02.032
