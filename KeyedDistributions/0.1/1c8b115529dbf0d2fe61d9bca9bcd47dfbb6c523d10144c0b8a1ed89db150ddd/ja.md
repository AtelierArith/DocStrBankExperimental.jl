```
KeyedDistributions.KeyedSampleable(d<:Distributions.Sampleable, keys::Tuple{Vararg{AbstractVector}})
KeyedDistributions.KeyedSampleable(d<:Distributions.Sampleable; named_keys...)
```

`Distributions.Sampleable` `d`の各変量に対して`keys`（および`named_keys`キーワード引数を使用する場合はdimnames）を保存し、`Distributions.Sampleable`および`KeyedArray`の一般的な関数をすべてサポートします。

`rand`のような`AbstractArray`を返す一般的な関数は、`Distributions.Sampleable`から派生したキーとdimnamesを持つ`KeyedArray`を返します。

`keys`の型は[AxisKeys.jl](https://github.com/mcabbott/AxisKeys.jl)と一致するように制限されています。`keys`タプルの長さまたは`named_keys`の数は、1次元分布および多次元分布の場合は1、行列変量分布の場合は2である次元の数と等しくなければなりません。各キーのベクトルの長さは、各次元に沿った長さと一致する必要があります。

!!! note
    正確に周辺化できる分布については、KeyedDistributions.KeyedSampleableは`KeyedArray`と同様にインデックスまたはルックアップ構文を介して周辺化できます。つまり、特定のインデックスまたはキーを保持し、他のものを周辺化するために角括弧または丸括弧を使用できます。例えば、`D::KeyedMvNormal`が`:a, :b, :c`の場合：

      * `D(:a)`またはD[1]は`:b, :c`を周辺化し、`:a`の上に`KeyedNormal`を返します。
      * `D([:a])`またはD[[1]]は`:b, :c`を周辺化し、`:a`の上に`KeyedMvNormal`を返します。
      * `D([:a, :b])`または`D[[1, 2]]`は`:c`を周辺化し、`:a, :b`の上に`KeyedMvNormal`を返します。

