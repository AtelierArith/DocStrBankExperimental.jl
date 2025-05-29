```
predict([rng::AbstractRNG,] model::Model, chain::AbstractVector{<:AbstractVarInfo})
```

事後予測分布からサンプルを生成するには、`chain`で提供された各パラメータ値のセットで`model`を評価します。事後予測サンプルの数は`chain`の長さと一致します。返される`AbstractVarInfo`には、事後パラメータ値と予測値の両方が含まれます。
