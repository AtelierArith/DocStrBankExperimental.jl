```
as_array_size(args...) -> dims::Dims
```

は、配列の次元または範囲 `args...` を配列サイズの標準形式、すなわち `eltype(Dims)` のタプルに変換します。`args...` の中の任意の範囲は、その長さに置き換えられます。

配列の次元または範囲はタプルとしても提供できます。 [`RelaxedArrayShape{N}`](@ref) は、`as_array_size` が適用可能な `N`-タプルの型の和です。

また、[`as_array_shape`](@ref)、[`as_array_axes`](@ref)、[`as_array_dim`](@ref)、`Dims`、および [`new_array`](@ref) も参照してください。
