```
process(algo::Union{A, Type{A}}, param::AbstractImageReconstructionParameters, inputs...) where A <: AbstractImageReconstructionAlgorithm
```

アルゴリズム `algo` とパラメータ `param` を使用して `inputs` を処理します。処理ステップの結果を返します。`algo` のインスタンスに対して実装されていない場合、`algo` の型でデフォルトの実装が呼び出されます。
