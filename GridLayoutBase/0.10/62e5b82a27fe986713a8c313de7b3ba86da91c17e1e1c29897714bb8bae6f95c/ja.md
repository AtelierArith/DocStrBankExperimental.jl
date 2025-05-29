```
rowgap!(gl::GridLayout, i::Integer, s::Union{Fixed, Relative, Real})
rowgap!(gl::GridLayout, s::Union{Fixed, Relative, Real})
```

`gl`の行間を設定します。2つの引数のバージョンは、`gl`内のすべての行間を設定します。3つの引数のバージョンは、行`i`と`i+1`の間の行間を設定します。実数を`s`に渡すことは、`Fixed(s)`を渡すことと同じ動作をします。

関連情報として[Fixed](@ref)と[Relative](@ref)を参照してください。
