```
Dataset{L} <: DimensionalData.AbstractDimStack{L}
```

いくつかの次元を共有する次元配列のコンテナ。

この型は、`DimensionalData.DimStack`と同じインターフェースを実装し、同様の使用法を持つ[`DimensionalData.AbstractDimStack`](https://rafaqz.github.io/DimensionalData.jl/stable/reference/#DimensionalData.AbstractDimStack)です。

`Dataset`がPythonに渡されると、データをコピーすることなく`xarray.Dataset`に変換されます。つまり、PythonオブジェクトはJuliaオブジェクトと同じメモリを共有します。しかし、`xarray.Dataset`がJuliaに渡されると、そのデータはコピーされなければなりません。

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
