```
Dataset{K,T,N,L} <: DimensionalData.AbstractDimStack{K,T,N,L}
```

いくつかの次元を共有する次元配列のコンテナ。

この型は[`DimensionalData.AbstractDimStack`](@extref DimensionalData dimstacks)であり、`DimensionalData.DimStack`と同じインターフェースを実装し、同様の使用法を持っています。

# コンストラクタ

```
Dataset(data::DimensionalData.AbstractDimArray...)
Dataset(data::Tuple{Vararg{<:DimensionalData.AbstractDimArray}})
Dataset(data::NamedTuple{Keys,Vararg{<:DimensionalData.AbstractDimArray}})
Dataset(
    data::NamedTuple,
    dims::Tuple{Vararg{DimensionalData.Dimension}};
    metadata=DimensionalData.NoMetadata(),
)
```

ほとんどの場合、コンストラクタを直接使用するのではなく、[`convert_to_dataset`](@ref)を使用して`Dataset`を作成してください。
