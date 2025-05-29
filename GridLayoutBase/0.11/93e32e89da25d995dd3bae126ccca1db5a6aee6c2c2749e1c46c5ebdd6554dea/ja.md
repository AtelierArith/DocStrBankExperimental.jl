```
colgap!(gl::GridLayout, i::Integer, s::Union{Fixed, Relative, Real})
colgap!(gl::GridLayout, s::Union{Fixed, Relative, Real})
```

`gl`の列の間隔を設定します。2つの引数のバージョンは、`gl`内のすべての列の間隔を設定します。3つの引数のバージョンは、列`i`と`i+1`の間の間隔を設定します。実数を`s`に渡すことは、`Fixed(s)`を渡すことと同じ動作をします。

関連情報として[Fixed](@ref)と[Relative](@ref)を参照してください。
