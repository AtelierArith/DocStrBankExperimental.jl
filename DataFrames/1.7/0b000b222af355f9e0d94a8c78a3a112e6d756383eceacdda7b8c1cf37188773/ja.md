```
DataFrameRows{D<:AbstractDataFrame} <: AbstractVector{DataFrameRow}
```

`AbstractDataFrame`の行を反復処理するイテレータで、各行は`DataFrameRow`として表されます。

この型の値は[`eachrow`](@ref)関数によって返されます。
