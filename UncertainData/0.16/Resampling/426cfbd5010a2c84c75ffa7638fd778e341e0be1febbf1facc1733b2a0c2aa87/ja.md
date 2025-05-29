```
resample(x, ssc::SequentialSamplingConstraint)
resample(x, ssc::SequentialSamplingConstraint, c)
resample(x::UncertainIndexValueDataset, ssc::SequentialSamplingConstraint, ic, vc)
```

`x`を要素ごとにサンプリングし、サンプルが`ssc`によって与えられた逐次制約に従うようにします。あるいは、逐次サンプリングが行われる*前に*制約`c`を`x`に適用します。

サンプリングの前に、そのようなシーケンスが存在するかを確認するチェックが行われます。チェックが行われる前に、`x`の分布は`c`によって提供された分位点に要素ごとに切り捨てられ、有限のサポートを持つことが保証されます。

`x`が不確実なインデックス値データセットである場合、逐次制約はインデックスにのみ適用されます。追加の制約のセットが不確実なインデックス値データセットに追加されると、それらはインデックスと値の両方に適用されます。また、別々のインデックス制約`ic`と値制約`vc`を指定することも可能です。

制約`c`、または`ic`と`vc`が与えられた場合、`c`/`ic`/`vc`は単一の制約であるか、制約が`x`の分布に要素ごとに適用される制約のベクトルでなければなりません。

```
resample!(s, x, ssc::SequentialSamplingConstraint, lqs, uqs)
```

上記と同様ですが、サンプリングされた値を事前に割り当てられたベクトル`s`に格納します。ここで、`length(x) == length(s)`です。これにより、繰り返しサンプリング中の過剰なメモリ割り当てを回避します。これには、初期の切り捨てステップのために要素ごとの下限分位点`lqs`と上限分位点`uqs`を事前に計算する必要があります。

このメソッドは、`x`における厳密に増加するシーケンスの存在を*チェックしません*。それを確認するには、[`sequence_exists`](@ref)を使用してください。

関連情報: [`sequence_exists`](@ref)、[`StrictlyIncreasing`](@ref)、[`StrictlyDecreasing`](@ref)、[`StartToEnd`](@ref)。

## 例

```julia
N = 100
t = [UncertainValue(Normal, i, 2) for i in 1:N];
resample(t, StrictlyIncreasing(StartToEnd()))
```

```julia
N = 100
t = [UncertainValue(Normal, i, 2) for i in 1:N];

# `t`を通じて増加するシーケンスが存在するか確認
c = StrictlyIncreasing(StartToEnd())
exists, lqs, uqs = sequence_exists(t, c)

# サンプルベクトルを事前に割り当て
s = zeros(Float64, N)

if exists
    for i = 1:100
        resample!(s, t, c)
        # sを使って何かをする
        # ...
    end
end
```
