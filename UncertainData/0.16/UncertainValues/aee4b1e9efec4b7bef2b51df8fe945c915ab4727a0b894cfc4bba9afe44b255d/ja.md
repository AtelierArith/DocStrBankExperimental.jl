```
UncertainScalarPopulation(values, probs)
UncertainScalarPopulation(values, probs::Vector{Number})
UncertainScalarPopulation(values, probs::Statsbase.AbstractWeights)
```

`UncertainScalarPopulation`は、いくつかの集団メンバー（`values`）と、集団メンバーの相対的重要性を示すいくつかの重み（`probs`）で構成されています（例えば、再サンプリング中に）。

## フィールド

  * **`values`**: 集団のメンバー。数値、パッケージ内で定義された不確実な値の任意の型（集団を含む）、およびMeasurements.jlからの`Measurement`インスタンスであることができます。
  * **`probs`**: 集団の各メンバーをサンプリングする確率。

## コンストラクタ

  * `values`がスカラー数値のみを含む場合、`values`フィールドは`Vector{Number}`型になります。
  * `values`が1つ以上の不確実な値を含む場合、`values`フィールドは`Vector{AbstractUncertainValue}`型になります。

## 例

```julia

# CertainValues（スカラーはCertainValueに昇格）や理論分布、KDE分布からなる不確実な集団
pop1 = UncertainScalarPopulation(
    [3.0, UncertainValue(Normal, 0, 1), UncertainValue(Gamma, 2, 3), 
    UncertainValue(Uniform, rand(1000))], [0.5, 0.5, 0.5, 0.5])

# スカラー値からなる不確実な集団
pop2 = UncertainScalarPopulation([1, 2, 3], rand(3))
pop3 = UncertainScalarPopulation([1, 2, 3], Weights(rand(3)))

# 不確実な集団からなる不確実な集団
pop4 = UncertainScalarPopulation([pop1, pop2], [0.1, 0.5])

# 不確実な集団、不確実なスカラー、および正規分布からなる不確実な集団。ランダムな重みを割り当てる。
vals = [pop1, pop2, 2, UncertainValue(Normal, 0.3, 0.014)]
pop5 = UncertainScalarPopulation(vals, Weights(rand(4)))
```
