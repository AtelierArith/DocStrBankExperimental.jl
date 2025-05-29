```
ginisimpson(v::Union{AbstractVector, AbstractSparseMatrix}) 
ginisimpson(abt::AbstractAbundanceTable, overwrite=false)
```

ベクトルのためのジニ・シンプソンα多様性指標を計算します。`AbstractAbundanceTable`に対して呼び出すと、サンプルごとに1つのエントリを持つ1 x nsamples行列を返します。詳細は[`ginisimpson!`](@ref)を参照してください。
