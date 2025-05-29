```
flags(x::FlagSet)
```

`x`のフラグのセットを`Tuple`として返します。

# 例

```julia
julia> @symbol_flagset FontFlags bold=1 italic=2 large=4

julia> flags(FontFlags(3))
(:bold, :italic)
```
