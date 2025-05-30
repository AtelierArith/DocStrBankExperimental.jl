```julia
DGLDDRK73_C(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
              step_limiter! = OrdinaryDiffEq.trivial_limiter!,
              thread = OrdinaryDiffEq.False(),
              williamson_condition = true)
```

明示的ルンゲ-クッタ法。7段階、3次の低ストレージ・低減衰・低分散スキームで、波動伝播問題に適用される不連続ガレルキン空間離散化のためのもの。計算領域の幾何学的特徴により最大空間ステップが小さい場合にPDE離散化のために最適化されています。固定タイムステップのみ。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャストが直列（`thread = OrdinaryDiffEq.False()`）であるべきか、複数のスレッドを使用すべきか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。
  * `williamson_condition`: ブロードキャスト式と関数呼び出し `f` を融合させる最適化を可能にします。ただし、`Array` 型にのみ機能します。

## 参考文献

T. Toulorge, W. Desmet.     不連続ガレルキン空間離散化のための最適ルンゲ–クッタスキーム     波動伝播問題に適用される。     計算物理学ジャーナル, 231(4), pp 2067-2091, 2012.     doi: https://doi.org/10.1016/j.jcp.2011.11.024
