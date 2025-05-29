```
findkU(d::UnivariateDistribution, spec::MSetting)
findkU(d::dPower, spec::MSetting)
updatekU(d::UnivariateDistribution, spec::MSetting)
updatekU(d::dPower, spec::MSetting)
```

M推定における下限調整定数を見つける関数で、下限調整定数が与えられたと仮定します。Xの分布が`d`である場合、$Z = (X - E(X))/std(X)$を解きます。`d`が単変量分布の場合、`d`が`dPower`型の場合は$Z = (X1 i - E(X^i))/std(X^i)$です。

`findkU`は上限調整定数を返し、`updatekU`は更新された仕様`spec`を返します。

仕様が`HampelSetting`の場合、スカラーではなく下限調整定数ベクトル`kL`があります。この関数は、適切なスカラー`c`に対して`c ⋅ kL`を検索します。

# 例

```julia
d = Poisson(10)
spec = Huber(0.5)
findkU(d, spec)
```

[`dPower`](@ref dPower)も参照してください。
