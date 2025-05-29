```
ManifoldProximalMapObjective{E<:AbstractEvaluationType, TC, TP, V <: Vector{<:Integer}} <: AbstractManifoldCostObjective{E, TC}
```

近接マップの評価に基づいてソルバーのための問題を指定します。

# フィールド

  * `cost` - 最小化する関数 $F:\mathcal M→ℝ$
  * `proxes` - 近接マップ $\operatorname{prox}_{λ\varphi}:\mathcal M→\mathcal M$ としての関数 `(M, λ, p) -> q`。
  * `number_of_proxes` - （`ones(length(proxes))`` 各関数の近接マップの数。近接マップ関数が関数ごとに複数のエントリを返すような結合されたマップの一つである場合、この値を調整する必要があります。指定されていない場合、各関数につき1つの近接マップに設定されます。

# 参照

[`cyclic_proximal_point`](@ref), [`get_cost`](@ref), [`get_proximal_map`](@ref)
