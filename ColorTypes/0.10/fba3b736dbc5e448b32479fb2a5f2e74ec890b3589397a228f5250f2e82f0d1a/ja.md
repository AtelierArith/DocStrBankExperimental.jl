```
CT = color_type(C::Type)
CT = color_type(c::Colorant)
```

アルファチャンネルを無視して、Colorオブジェクトの型を返します。例えば、

```
color_type(RGB)          === RGB
color_type(RGB{Float32}) === RGB{Float32}
color_type(ARGB{N0f8})   === RGB{N0f8}
color_type(RGB(1,0,0))   === RGB{N0f8}
```

`color_type`や、[`base_color_type`](@ref)、[`base_colorant_type`](@ref)、[`ccolor`](@ref)のような関連関数は、汎用コードを書く際に型を操作するのに便利です。
