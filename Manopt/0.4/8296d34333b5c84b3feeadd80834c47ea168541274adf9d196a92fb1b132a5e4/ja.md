```
StopWhenGradientNormLess <: StoppingCriterion
```

現在の勾配ノルムに基づく停止基準。

# フィールド

  * `norm`:      勾配 `X` のノルムを `M` 上の `p` での接空間で計算する関数 `(M::AbstractManifold, p, X) -> ℝ`
  * `threshold`: この値未満の距離で停止することを示すしきい値

# 内部フィールド

  * `last_change` 最後の変更を保存
  * `at_iteration` 停止指示が発生したイテレーションを保存

# コンストラクタ

```
StopWhenGradientNormLess(ε; norm=(M,p,X) -> norm(M,p,X))
```

勾配のしきい値 `ε` を持つ停止基準を作成します。つまり、この基準は [`get_gradient`](@ref) がノルムが `ε` 未満の勾配ベクトルを返すときに停止することを示します。使用するノルムは `norm=` キーワードで指定できます。
