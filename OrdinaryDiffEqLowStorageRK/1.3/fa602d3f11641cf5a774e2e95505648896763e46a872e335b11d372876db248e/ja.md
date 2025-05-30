```julia
SHLDDRK64(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False(),
            williamson_condition = true)
```

明示的ルンゲ-クッタ法。4次、6段階の低ストレージ法。固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `williamson_condition`: ブロードキャスト式と関数呼び出し `f` を融合させる最適化を可能にします。ただし、`Array` 型にのみ機能します。

## 参考文献

D. Stanescu, W. G. Habashi.     2N-ストレージ低消散および分散ルンゲ-クッタスキームによる計算音響学。     計算物理学ジャーナル, 143(2), pp 674-681, 1998.     doi: https://doi.org/10.1006/jcph.1998.5986     }
