```
MomentumOptimizer(η, α)
```

モーメンタムオプティマイザのインスタンスを作成します。

モーメンタムオプティマイザは、[`GradientOptimizer`](@ref)に似ています。ただし、過去の履歴を保存する非自明なキャッシュがあります（[`MomentumCache`](@ref）を参照）。キャッシュは次のように更新されます：

$$
    B^{\mathrm{cache}} \gets \alpha{}B^{\mathrm{cache}} + \nabla_\mathrm{weights}L
$$

そして、最終的な速度は次のように計算されます。

$$
    \mathrm{velocity} \gets  - \eta{}B^{\mathrm{cache}}.
$$

# 実装

メモリを節約するために、*velocity*は入力の$\nabla_WL$に保存されます。これは、[`GradientOptimizer`](@ref)の場合と似ています。
