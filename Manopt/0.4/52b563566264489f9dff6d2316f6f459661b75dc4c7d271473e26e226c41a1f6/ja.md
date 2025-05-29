```
get_cost(M::AbstractManifold, mco::AbstractManifoldCostObjective, p)
```

[`AbstractManifoldCostObjective`](@ref)内のコスト関数を`M`の`p`で評価します。

デフォルトでは、この実装はコストが`mco.cost`内に格納されていると仮定しています。
