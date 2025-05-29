```
StatisticalMeasuresBase.multimeasure(atomic_measure; options...)
```

新しい測定値、*マルチ測定*を返します。これは、予測ターゲットペア `(ŷ, y)` に対して、`atomic_measure` を `MLUtils.eachobs((ŷ, y))` に対してブロードキャストし、結果を集約します。ここで `ŷ` と `y` は、必ず `MLUtils` の `getobs/numobs` インターフェースを実装するオブジェクト（配列や、`Tables.istable(X) == true` であるテーブル `X` など）です。

すべてのマルチ測定は自動的に重みとクラス重みをサポートします。

デフォルトでは、集約は `atomic_measure` の好ましいモードを使用して行われます。すなわち、`StatisticalMeasuresBase.external_aggregation_mode(atomic_measure)` です。内部的には、[`aggregate`](@ref) メソッドを使用して集約が行われます。

`multimeasure` のネストされた適用は、行列や一部のテーブル（「マルチターゲット」）および多次元配列に適用される測定を構築するのに便利です。以下の高度な例を参照してください。

# 簡単な例

```julia
using StatisticalMeasuresBase

# 原子測定を定義します：
struct L2OnScalars end
(::L2OnScalars)(ŷ, y) = (ŷ - y)^2

julia> StatisticalMeasuresBase.external_aggregation_mode(L2OnScalars())
Mean()

# マルチ測定を定義します：
L2OnVectors() = StatisticalMeasuresBase.multimeasure(L2OnScalars())

y = [1, 2, 3]
ŷ = [7, 6, 5]
@assert L2OnVectors()(ŷ, y) ≈ (ŷ - y).^2 |> mean
```

# キーワードオプション

  * `mode=StatisticalMeasuresBase.external_aggregation_mode(atomic_measure)`: ブロードキャストの結果を集約するためのモード。可能な値には `Mean()` や `Sum()` が含まれます。すべてのオプションとその意味については [`AggregationMode`](@ref) を参照してください。重みと一緒に `Mean()` を使用すると、通常の重み付き平均が平均重み値でスケーリングされて返されます。
  * `transform=identity`: 各 `atomic_measure` 呼び出しに渡す前に `y` と `ŷ` の観測に適用されるオプションの変換。便利な値は `vec∘collect` で、これはベクトルに対しては恒等で、配列をフラット化し、一部のテーブルの観測（「行」）をベクトルに変換します。以下の例を参照してください。
  * `atomic_weights=nothing`: 各 `(ŷᵢ, yᵢ)` に対して、`(transform(ŷᵢ), transform(yᵢ))` のペアを評価するために原子測定に渡される重み。`MLUtils.eachjobs(ŷ, y)` の各呼び出しに対して行われます。`atomic_measure` が重みをサポートしていると仮定します。
  * `skipnan=false`: 集約時に `NaN` 値をスキップするかどうか（`missing` 値は常にスキップされます）

# 高度な例

上記で定義した `L2OnVectors` に基づいて：

```julia
# 多次元配列と一部のテーブルのための測定を定義します：
L2() = multimeasure(L2OnVectors(), transform=vec∘collect)

y = rand(3, 5, 100)
ŷ = rand(3, 5, 100)
weights = rand(100)
@assert L2()(ŷ, y, weights) ≈
   sum(vec(mean((ŷ - y).^2, dims=[1, 2])).*weights)/length(weights)

using Tables
y = rand(3, 100)
ŷ = rand(3, 100)
t = Tables.table(y') |> Tables.rowtable
t̂ = Tables.table(ŷ') |> Tables.rowtable
@assert L2()(t̂, t, weights) ≈
   sum(vec(mean((ŷ - y).^2, dims=1)).*weights)/length(weights)
```

!!! note
    測定特性 [`StatisticalMeasuresBase.observation_scitype(measure)`](@ref)（デフォルト=`Union{}`）および [`StatisticalMeasuresBase.can_consume_tables(measure)`](@ref)（デフォルト=`false`）は原子測定から転送されず、`multimeasure` を使用してラップされた測定に対して明示的にオーバーロードする必要があります。

