```
colgap!(gl::GridLayout, i::Integer, s::Union{Fixed, Relative, Real})
colgap!(gl::GridLayout, s::Union{Fixed, Relative, Real})
```

`gl`の列の間隔を設定します。2つの引数のバージョンは、`gl`内のすべての列の間隔を設定します。3つの引数のバージョンは、列`i`と`i+1`の間の間隔を設定します。`s`に実数を渡すことは、`Fixed(s)`を渡すことと同じ動作をします。

[Fixed](@ref)および[Relative](@ref)も参照してください。
