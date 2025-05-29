```
ManifoldCostObjective{T, TC} <: AbstractManifoldCostObjective{T, TC}
```

コスト関数 $f:  \mathbb M → ℝ$ に関する情報のみを持つ [`AbstractManifoldObjective`](@ref) を指定します。これは、マンifold `M` 上の点 `p` でコスト値 `c` を計算する関数 `(M, p) -> c` として実装されています。

  * `cost`: 最小化する関数 $f: \mathcal M → ℝ$

# コンストラクタ

```
ManifoldCostObjective(f)
```

問題を生成します。この問題には割り当て関数はありませんが、一貫性の理由から型 `T` を他の問題と合わせて設定できます。

# 使用例

[`NelderMead`](@ref), [`particle_swarm`](@ref)
