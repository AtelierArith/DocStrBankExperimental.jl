```
Measure(m)
```

測定のようなオブジェクト `m` を、StatisticalMeasuresBase.jl の意味での測定に変換します。定義については [`StatisticalMeasuresBase.is_measure`](@ref) を参照してください。

通常、`Measure` は、StatisticalMeasuresBase.jl によって指定された呼び出し動作とは異なる事前に存在する動作を持つ測定に適用されます。

# 新しい実装

`Measure` にラップ可能なタイプ `M` の測定のようなオブジェクトを作成するには、以下の適切なメソッドを実装してください。最初と最後は必須です。

```
(m::Measure{M})(ŷ, y)
(m::Measure{M})(ŷ, y, weights)
(m::Measure{M})(ŷ, y, class_weights::AbstractDict)
(m::Measure{M}, ŷ, y, weights, class_weights)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, weights)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, class_weights::AbstractDict)
StatisticalMeasuresBase.measurements(m::Measure{M}, ŷ, y, weights, class_weights)
StatisticalMeasuresBase.is_measure(m::Measure{M}) where M = true
```

実装の中で、[`StatisticalMeasuresBase.unwrap`](@ref) を使用して、ラップされていないオブジェクトにアクセスできます。すなわち、`StatisticalMeasuresBase.unwrap(Measure(m)) === m` です。

# サンプル実装

`abs` 関数をラップして、差の絶対値を計算する測定として使用するには：

```
import StatisticalMeasuresBase as API

(measure::API.Measure{typeof(abs)})(yhat, y) = API.unwrap(measure)(yhat - y)
API.is_measure(::API.Measure{typeof(abs)}) = true

julia> API.Measure(abs)(2, 5)
3
```
