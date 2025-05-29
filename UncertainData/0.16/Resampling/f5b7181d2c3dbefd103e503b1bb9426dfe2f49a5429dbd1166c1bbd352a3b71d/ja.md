```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{UncertainScalarKDE}) -> UncertainIndexValueDataset
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedResampling{UncertainScalarPopulation}) -> UncertainIndexValueDataset
```

`x`の各要素を`binning.n`で与えられた回数だけ再サンプリングします。再サンプリング後、値をそのインデックスに従って、`binning.left_bin_edges`で与えられたビンに分配します。

## 戻り値

`UncertainIndexValueDataset`を返します。インデックスは各ビン内で均等に分布していると仮定され、ビンの中心で`CertainValue`として表されます。データセットの値は、`binning`によって異なる表現を持ちます：

  * `binning`が`BinnedResampling{UncertainScalarKDE}`の場合、各ビンの値は、そのビンに落ちる再サンプリングされたインデックスの再サンプリングされた値の分布に対するカーネル密度推定によって表されます。
  * `binning`が`BinnedResampling{UncertainScalarPopulation}`の場合、各ビンの値は、ビンに落ちる再サンプリングされたインデックスの再サンプリングされた値からなる等確率の集団によって表されます。
