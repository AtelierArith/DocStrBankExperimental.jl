```
CommunityProfile{T, F, S} <: AbstractAbundanceTable{T, F, S}
```

`AbstractAssemblage`は、[EcoBase.jl](https://github.com/EcoJulia/EcoBase.jl)からのもので、内部で`SparseMatrixCSC`を使用しています。

`CommunityProfile`は、`AbstractFeature`でインデックスされた行と`AbstractSample`でインデックスされた列を持つテーブルです。注意 - サンプルと特徴の`name`を使用してインデックスを付けることができます。
