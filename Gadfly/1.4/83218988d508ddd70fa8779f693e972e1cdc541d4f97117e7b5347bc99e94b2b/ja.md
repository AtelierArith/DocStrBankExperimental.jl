```
spy(M::AbstractMatrix, elements::ElementOrFunction...; mapping...) -> Plot
```

`M`のヒートマップをプロットします。`M[1,1]`は左上に配置されます。`NaN`の値は空白のままとなり、`M`のすべての要素が`NaN`の場合はエラーが発生します。[`Geom.rectbin`](@ref)および[`Coord.cartesian(fixed=true)...)`](@ref Gadfly.Coord.cartesian)を参照してください。
