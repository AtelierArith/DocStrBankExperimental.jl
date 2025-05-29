```
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedWeightedResampling{UncertainScalarKDE}) -> UncertainIndexValueDataset
bin(x::AbstractUncertainIndexValueDataset, binning::BinnedWeightedResampling{UncertainScalarPopulation}) -> UncertainIndexValueDataset
```

`x`の各要素を指定された回数だけ再サンプリングします。再サンプリング後、値をそのインデックスに従って、`binning.left_bin_edges`で定義された`N-1`要素のグリッドによって与えられた`N`個のビンに分配します。合計で、`length(x)*binning.n`の引き出しがビンに分配されます。`x[i]`が再サンプリングされる正確な回数は、`binning.weights[i]`によって与えられます（確率重みは常に1に正規化されます）。

## 戻り値

`UncertainIndexValueDataset`を返します。インデックスは各ビン内で均等に分布していると仮定され、ビンの中心で`CertainValue`として表されます。データセットの値は、`binning`が何であるかによって異なる表現を持ちます：

  * `binning`が`BinnedWeightedResampling{UncertainScalarKDE}`の場合、各ビンの値は、そのビンに落ちる再サンプリングされた値の分布に対するカーネル密度推定によって表されます。
  * `binning`が`BinnedWeightedResampling{UncertainScalarPopulation}`の場合、各ビンの値は、そのビンに落ちる再サンプリングされた値からなる等確率の集団によって表されます。
