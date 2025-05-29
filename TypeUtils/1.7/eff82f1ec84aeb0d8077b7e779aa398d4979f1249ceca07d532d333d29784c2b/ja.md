```
as_array_shape(args...) -> r::Union{Dims,ArraysAxes}
```

は、配列の次元または範囲 `args...` を配列の形状の標準形式に変換します。これは次のいずれかです：

  * 配列のサイズ、すなわち `Int` のタプルです。これは、すべての `args...` が整数または `Base.OneTo` のインスタンスである場合の結果であり、後者は存在する場合、その長さに置き換えられます。
  * 配列の軸、すなわち `AbstractUnitRange{Int}` のタプルです。これは、`args...` のいずれかが非 `Base.OneTo` 範囲である場合の結果であり、整数は `Base.OneTo{eltype(Dims)}` のインスタンスに変換されます。

配列の次元または範囲はタプルとしても提供できます。 [`RelaxedArrayShape{N}`](@ref) は、`as_array_shape` が適用可能な `N`-タプルの型の和です。

また、[`as_array_size`](@ref)、[`as_array_axes`](@ref)、[`ArrayAxes`](@ref)、`Dims`、および [`new_array`](@ref) も参照してください。
