```
CollectionDomain{T <: InfiniteScalarDomain} <: InfiniteArrayDomain
```

`InfiniteScalarDomain`のコレクションを格納する`DataType`であり、その形式に従う無限パラメータのコレクションを特徴づけます。これは[`DependentParameters`](@ref)と一緒に使用するためのものです。

**フィールド**

  * `domains::Array{T}` スカラー領域のコレクション。
