```
PlugIn(e::InformationMeasure) <: DiscreteInfoEstimatorGeneric
```

`PlugIn`推定量は経験的/単純/"最大尤度"推定量とも呼ばれ、任意の離散[`InformationMeasure`](@ref)に対して[`information`](@ref)と共に使用されます。

これは、与えられた式によって正確に任意の量を計算します。情報量を計算する際、ここでは確率の関数として定義されており、最大尤度から導出された確率質量関数から直接量を計算します（[`RelativeAmount`](@ref)の確率の推定値）。

## プラグイン推定量のバイアス

[`Shannon`](@ref)エントロピーのプラグイン推定量は真のエントロピーを過小評価し、そのバイアスは異なる[`outcomes`](@ref)の数が増えるにつれて大きくなります（Arora et al., 2022)[Arora2022](@cite)、

$$
bias(H_S^{plugin}) = -\dfrac{K-1}{2N} + o(N^-1).
$$

ここで、`K`は異なる結果の数、`N`はサンプルサイズです。多くの著者が、代替のShannonエントロピー推定量を提案することでこれを改善しようとしました。例えば、[`MillerMadow`](@ref)推定量は、上記のバイアス項を戻す単純な修正です。他にも多くの推定量が存在します; 概要については[`DiscreteInfoEstimator`](@ref)sを参照してください。
