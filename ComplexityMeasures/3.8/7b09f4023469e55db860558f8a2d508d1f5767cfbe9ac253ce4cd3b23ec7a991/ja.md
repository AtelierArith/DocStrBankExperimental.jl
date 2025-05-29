```
SequentialPairDistances <: CountBasedOutcomeSpace
SequentialPairDistances(x::AbstractVector; n = 3, metric = Chebyshev(), m = 3, τ = 1)
SequentialPairDistances(x::AbstractStateSpaceSet; n = 3, metric = Chebyshev())
```

連続した点のペアの距離の分布に基づく結果空間。

この結果空間は、もちろんここで再現できる「分布エントロピー」の一部として暗黙的に現れます（以下の例を参照）。私たちは、この方法を任意の [`InformationMeasure`](@ref) および [`DiscreteInfoEstimator`](@ref) と、Distances.jl からの有効な距離 `metric` で使用できるように一般化しました。

初期化には入力データ `x` が必要です。なぜなら、ペア間距離の分布をビン分けするために必要な最小/最大距離を知るために距離を事前に計算する必要があるからです。入力が `AbstractVector` の場合、ベクトルは距離を計算する前に埋め込まれます。入力が `AbstractStateSpaceSet` の場合、埋め込みステップはスキップされ、距離は各状態ベクトル `xᵢ ∈ x` に対して直接計算されます。

## 説明

`SequentialPairDistances` は以下のことを行います：

  * 入力時系列 `x` を、まず埋め込み次元 `m` と埋め込みラグ `τ` を使用して埋め込むことによって変換します（または、入力がすでに埋め込まれている場合はこのステップをスキップします）。
  * 与えられた `metric` に従って、連続した点のペア間の距離 `ds` を計算します。
  * 区間 `[minimum(ds), maximum(ds)]` を `n` 個の等サイズのビンに分割し、[`RectangularBinEncoding`](@ref) を使用して、これらのビンに距離をマッピングします。

## 結果空間

`SequentialPairDistances` の結果空間 `Ω` は、ペア間距離がマッピングされるビンであり、整数 `1:n` としてエンコードされています。実際のビン座標が必要な場合、これらは [`decode`](@ref) を使用して回復できます（以下の例を参照）。

## 実装

  * [`codify`](@ref)。入力 `x` は `codify` を呼び出す際に無視されることに注意してください。なぜなら、入力データは `SequentialPairDistances` を構築する際にすでに処理されているからです。

## 例

結果ビンは以下のように取得できます。

```julia
using ComplexityMeasures
x = rand(100)
o = SequentialPairDistances(x)
cts, outs = counts_and_outcomes(o, x)
```

距離ヒストグラムのために `n = 3` ビンで「分布エントロピー」を計算します：

```julia
using ComplexityMeasures
x = rand(1000000)
o = SequentialPairDistances(x, n = 3, metric = Chebyshev()) # 元の論文からの metric
h = information(Shannon(base = 2), o, x)
```
