```
ChaoShen <: DiscreteInfoEstimatorShannon
ChaoShen(definition::Shannon = Shannon())
```

`ChaoShen`推定量は、[`information`](@ref)と共に使用され、[Chao2003](@citet)に従って離散[`Shannon`](@ref)エントロピーを計算します。

## 説明

この推定量は、各プラグイン確率推定値にサンプルカバレッジの推定値を掛ける[`HorvitzThompson`](@ref)推定量の修正です。もし$f_1$が長さ$N$のサンプルにおけるシングルトン（1回だけ発生する結果）の数であれば、サンプルカバレッジは$C = 1 - \dfrac{f_1}{N}$です。Chao-Shen推定量のShannonエントロピーは次のようになります。

$$
H_S^{CS} = -\sum_{i=1}^M \left( \dfrac{C p_i \log(C p_i)}{1 - (1 - C p_i)^N} \right),
$$

ここで、$N$はサンプルサイズ、$M$は[`outcomes`](@ref)の数です。もし$f_1 = N$であれば、$f_1$は正のエントロピーを確保するために$f_1 = N - 1$に設定されます[Arora2022](@cite)。
