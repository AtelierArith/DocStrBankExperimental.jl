```
findkL(d::UnivariateDistribution, spec::MSetting)
findkL(d::dPower, spec::MSetting)
updatekL(d::UnivariateDistribution, spec::MSetting)
updatekL(d::dPower, spec::MSetting)
```

M推定において上限調整定数が与えられたときに下限調整定数を見つける関数。Xの分布が`d`であると仮定し、E(ψ(Z)) = 0を解きます。ここで、$Z = (X - E(X))/std(X)$は`d`が単変量分布の場合、`d`がタイプ`dPower`の場合は$Z = (X1 i - E(X^i))/std(X^i)$です。

`findkL`は下限調整定数を返し、`updatekL`は更新された仕様`spec`を返します。

仕様が`HampelSetting`の場合、スカラーではなく上限調整定数ベクトル`kU`があります。この関数は、適切なスカラー`c`に対して`c ⋅ kU`を検索します。

# 例

```julia
d = Poisson(10)
spec = Huber(1.5)
findkL(d, spec)
```

さらに[`dPower`](@ref dPower)を参照してください。
