```
BubbleEntropy <: ComplexityEstimator
BubbleEntropy(; m = 3, τ = 1, definition = Renyi(q = 2))
```

`BubbleEntropy`複雑性推定器[Manis2017](@cite)は、各々が[`BubbleSortSwaps`](@ref)の結果空間を用いて計算された2つのエントロピーの差です。埋め込み次元はそれぞれ`m + 1`と`m`です。

[Manis2017](@citet)は、情報量の定義として`q = 2`の[`Renyi`](@ref)エントロピーを使用していますが、ここでは任意の[`InformationMeasure`](@ref)を使用できます。[Manis2017](@citet)は「バブルエントロピー」を以下の正規化された測定として定式化していますが、ここでは非正規化された測定も計算できます。

## 定義

入力データ`x`に対して、「バブルエントロピー」は、まず埋め込み次元`m`と埋め込み遅延`τ`を使用して入力データを埋め込み（埋め込まれた点を`y`と呼ぶ）、次に2つのエントロピーの差を計算することによって計算されます：

$$
BubbleEn_T(τ) = H_T(y, m + 1) - H_T(y, m)
$$

ここで、$H_T(y, m)$および$H_T(y, m + 1)$は、入力データ`x`が次元$m$および$m+1$に埋め込まれたときに計算されるタイプ$T$（例：[`Renyi`](@ref)）のエントロピーです。この非正規化バージョンを計算するには[`complexity`](@ref)を使用します。エントロピーの正規化された差を計算するには[`complexity_normalized`](@ref)を使用します：

$$
BubbleEn_H(τ)^{norm} = 
\dfrac{H_T(x, m + 1) - H_T(x, m)}{max(H_T(x, m + 1)) - max(H_T(x, m))},
$$

ここで、次元`m`および`m + 1`のエントロピーの最大値は[`information_maximum`](@ref)を使用して計算されます。

## 例

```julia
using ComplexityMeasures
x = rand(1000)
est = BubbleEntropy(m = 5, τ = 3)
complexity(est, x)
```
