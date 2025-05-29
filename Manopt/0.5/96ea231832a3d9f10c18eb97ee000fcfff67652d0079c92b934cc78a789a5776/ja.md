```
ManifoldSubgradientObjective{T<:AbstractEvaluationType,C,S} <:AbstractManifoldCostObjective{T, C}
```

サブグラディエントに基づく最適化問題の目的に関する情報を格納する構造体

# フィールド

  * `cost`:        最小化される関数 $f$
  * `subgradient`: 関数 $f$ のサブグラディエント $∂f$ を返す関数

# コンストラクタ

```
ManifoldSubgradientObjective(f, ∂f)
```

サブグラディエント目的のための [`ManifoldSubgradientObjective`](@ref) を生成します。これは、関数 `f(M, p)` と、マンフォールド `M` 上の点 `p` でサブ微分から必ずしも決定論的でない要素を返す関数 `∂f(M, p)` から構成されます。
