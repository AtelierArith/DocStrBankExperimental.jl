```
Dataset{L} <: DimensionalData.AbstractDimStack{L}
```

Container of dimensional arrays sharing some dimensions.

This type is an [`DimensionalData.AbstractDimStack`](https://rafaqz.github.io/DimensionalData.jl/stable/reference/#DimensionalData.AbstractDimStack) that implements the same interface as `DimensionalData.DimStack` and has identical usage.

When a `Dataset` is passed to Python, it is converted to an `xarray.Dataset` without copying the data. That is, the Python object shares the same memory as the Julia object. However, if an `xarray.Dataset` is passed to Julia, its data must be copied.

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
