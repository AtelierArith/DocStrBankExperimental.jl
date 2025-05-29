```
bigmat,bigmatasm,bigvecasm,bigvecdis = prepare(pattern)
```

スパースブロックを大きなスパース行列に組み立てる準備をします。 `bigmat` は、正しいスパース構造で割り当てられますが、その `nzval` は未定義です。 同じスパース構造を共有するブロックがある場合、`pattern` の `blocks` には `===` 要素を持つことができます。

`pattern` は `SparseMatrixCSC{<:SparseMatrixCSC}` であり、空のブロックは構造的にゼロです。

また、[`addin!`](@ref)も参照してください。
