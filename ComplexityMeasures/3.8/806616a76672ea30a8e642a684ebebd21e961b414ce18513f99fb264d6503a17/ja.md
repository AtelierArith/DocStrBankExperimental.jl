```
Jackknife <: DiscreteInfoEstimatorGeneric
Jackknife(definition::InformationMeasure = Shannon())
```

`Jackknife`推定量は、任意の離散[`InformationMeasure`](@ref)を計算するために[`information`](@ref)と共に使用されます。

`Jackknife`推定量は、バイアスを減少させるために一般的なジャックナイフ原理を使用します。[Zahl1977](@citet)は、[`Shannon`](@ref)エントロピー推定の文脈でジャックナイフ技術を初めて適用しました。ここでは、彼の推定量を任意の[`InformationMeasure`](@ref)で動作するように一般化しました。

## 説明

ジャックナイフ技術の例として、[`Shannon`](@ref)エントロピーのジャックナイフ推定の公式は次のとおりです。

$$
H_S^{J} = N H_S^{plugin} - \dfrac{N-1}{N} \sum_{i=1}^N {H_S^{plugin}}^{-\{i\}},
$$

ここで、$N$はサンプルサイズ、$H_S^{plugin}$はShannonエントロピーのプラグイン推定、${H_S^{plugin}}^{-\{i\}}$は$i$-thサンプルを除外して計算されたプラグイン推定です。
