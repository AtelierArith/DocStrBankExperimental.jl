```
process(algo::Union{A, Type{A}}, param::AbstractUtilityReconstructionParameters{P}, inputs...) where {A <: AbstractImageReconstructionAlgorithm, P <: AbstractImageReconstructionParameters}
```

アルゴリズム `algo` を使用して `inputs` を処理し、引数が `P` に与えられたかのように結果を返します。ユーティリティ `process` の例には、キャッシングやリモート実行を提供するプロセスがあります。
