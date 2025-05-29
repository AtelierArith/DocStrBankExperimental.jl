```
ManifoldProximalMapObjective{E<:AbstractEvaluationType, TC, TP, V <: Vector{<:Integer}} <: AbstractManifoldCostObjective{E, TC}
```

近接マップの評価に基づいてソルバーのための問題を指定します。これはコスト関数 $f$ の和項 $f = f_1 + f_2+ … + f_N$ に対する近接マップ $\operatorname{prox}_{λf_i}$ を表します。

# フィールド

  * `cost`: 最小化する関数 $f:\mathcal M→ℝ$
  * `proxes`: 近接マップ $\operatorname{prox}_{λf_i}:\mathcal M → \mathcal M$ としての関数 `(M, λ, p) -> q` またはインプレース `(M, q, λ, p)`。
  * `number_of_proxes`: 関数ごとの近接マップの数。近接マップ関数が関数ごとに複数のエントリを返すような結合されたマップの一つがある場合、この値を調整する必要があります。指定されていない場合、関数ごとに1つの近接マップに設定されます。

# コンストラクタ

```
ManifoldProximalMapObjective(f, proxes_f::Union{Tuple,AbstractVector}, numer_of_proxes=onex(length(proxes));
   evaluation=Allocating)
```

タプルまたはベクトルの関数を持つ近接問題を生成します。デフォルトでは、すべての関数が $f$ の1つの成分の単一の近接を計算します。

```
ManifoldProximalMapObjective(f, prox_f); evaluation=Allocating)
```

$$
f
$$

とその近接マップ $\operatorname{prox}_{λf}$ のための近接目的を生成します。

# 参照

[`cyclic_proximal_point`](@ref), [`get_cost`](@ref), [`get_proximal_map`](@ref) ```
