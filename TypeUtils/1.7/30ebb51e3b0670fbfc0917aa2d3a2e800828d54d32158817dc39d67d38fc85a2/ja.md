```
as_array_axes(args...) -> rngs::ArrayAxes
```

は、配列の次元または範囲 `args...` を配列軸の標準形式、すなわち `AbstractUnitRange{eltype(Dims)}` のタプルに変換します。`args...` の中の任意の整数は、`Base.OneTo{eltype(Dims)}` のインスタンスに置き換えられます。

配列の次元または範囲はタプルとしても提供できます。 [`RelaxedArrayShape{N}`](@ref) は、`as_array_axes` が適用可能な `N`-タプルの型の和集合です。

また、[`as_array_shape`](@ref)、[`as_array_size`](@ref)、[`as_array_axis`](@ref)、[`ArrayAxes`](@ref)、`Dims`、および [`new_array`](@ref) も参照してください。
