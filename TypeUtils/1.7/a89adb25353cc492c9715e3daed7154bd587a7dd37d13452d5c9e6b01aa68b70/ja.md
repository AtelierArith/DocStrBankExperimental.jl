```
RelaxedArrayShape{N}
```

は [`ArrayShape{N}`](@ref) に似ていますが、`AbstractRange{<:Integer}}}` も含まれています（`AbstractUnitRange{<:Integer}` だけではありません）。

メソッド [`as_array_shape`](@ref)、[`as_array_axes`](@ref)、および [`as_array_size`](@ref) は、`RelaxedArrayShape{N}` 型の任意の引数に対して呼び出すことができ、配列の軸またはサイズの標準形式に変換します。同様に、メソッド [`as_array_dim`](@ref) および [`as_array_axis`](@ref) は、`eltype(RelaxedArrayShape)` 型の任意の引数に対して呼び出すことができ、標準の配列次元の長さまたは軸に変換します。これらのメソッドはすべて、すべての範囲が単位ステップを持つことを確認します。

!!! warning
    Julia スタイルをよりよく反映する [`ArrayShape{N}`](@ref) を使用することが望ましいです。

