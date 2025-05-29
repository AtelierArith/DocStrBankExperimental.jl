```
KeyedDistributions.KeyedDistribution(d<:Distributions.Distribution, keys::Tuple{Vararg{AbstractVector}})
KeyedDistributions.KeyedDistribution(d<:Distributions.Distribution; named_keys...)
```

`Distributions.Distribution` `d` に対して、各変量の `keys`（および `named_keys` キーワード引数を使用する場合は dimnames）を保存します。これにより、`Distributions.Distribution` と `KeyedArray` の一般的な関数をすべてサポートします。

`rand` のような `AbstractArray` を返す一般的な関数は、`Distributions.Distribution` から派生したキーと dimnamesを持つ `KeyedArray` を返します。

`keys` の型は [AxisKeys.jl](https://github.com/mcabbott/AxisKeys.jl) と整合性があるように制限されています。`keys` タプルの長さまたは `named_keys` の数は、次元の数と等しくなければなりません。これは、単変量および多変量分布の場合は 1、行列変量分布の場合は 2 です。各キーのベクトルの長さは、各次元に沿った長さと一致する必要があります。

!!! note
    正確に周辺化できる分布については、KeyedDistributions.KeyedDistribution は、`KeyedArray` と同様にインデックス指定またはルックアップ構文を介して周辺化できます。つまり、特定のインデックスやキーを保持し、他のものを周辺化するために角括弧または丸括弧を使用できます。例えば、`D::KeyedMvNormal` に対して `:a, :b, :c` の場合：

      * `D(:a)` または D[1] は `:b, :c` を周辺化し、`:a` に対する `KeyedNormal` を返します。
      * `D([:a])` または D[[1]] は `:b, :c` を周辺化し、`:a` に対する `KeyedMvNormal` を返します。
      * `D([:a, :b])` または `D[[1, 2]]` は `:c` を周辺化し、`:a, :b` に対する `KeyedMvNormal` を返します。

