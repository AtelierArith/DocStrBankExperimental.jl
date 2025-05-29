```
colsize!(gl::GridLayout, i::Integer, s::Union{Aspect, Auto, Fixed, Relative, Real})
```

`gl`の`i`番目の列のサイズを設定します。すなわち、`gl[:, i]`です。`s`に実数を渡すことは、`Fixed(s)`を渡すことと同じ動作をします。

関連情報として、[Aspect](@ref)、[Auto](@ref)、[Fixed](@ref)、および[Relative](@ref)を参照してください。
