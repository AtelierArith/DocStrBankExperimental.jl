```
MillerMadow <: DiscreteInfoEstimatorShannon
MillerMadow(measure::Shannon = Shannon())
```

`MillerMadow`推定量は、[`information`](@ref)と共に使用され、[Miller1955](@citet)に従って離散[`Shannon`](@ref)エントロピーを計算します。

# 説明

Miller-Madow推定量のShannonエントロピーは次のように与えられます。

$$
H_S^{MM} = H_S^{plugin} + \dfrac{m - 1}{2N},
$$

ここで、$H_S^{plugin}$は[`PlugIn`](@ref)推定量を使用して推定されたShannonエントロピー、`m`は非ゼロ確率を持つビンの数（[Paninski2003](@citet)で定義されているように）、$N$は観測の数です。
