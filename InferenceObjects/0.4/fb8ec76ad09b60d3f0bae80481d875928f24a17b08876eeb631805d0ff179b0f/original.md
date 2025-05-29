```
Dataset{K,T,N,L} <: DimensionalData.AbstractDimStack{K,T,N,L}
```

Container of dimensional arrays sharing some dimensions.

This type is an [`DimensionalData.AbstractDimStack`](@extref DimensionalData dimstacks) that implements the same interface as `DimensionalData.DimStack` and has identical usage.

# Constructors

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

In most cases, use [`convert_to_dataset`](@ref) to create a `Dataset` instead of directly using a constructor.
