```
get_width(font::MonospaceBitmapASCIIFont)
```

モノスペースフォント `font` に含まれるグリフの j 軸（水平軸、2 番目の軸）に沿った幅を返します。

詳細は [`get_width`](@ref) を参照してください。

# 例

```julia-repl
julia> get_width(TERMINUS_32_16)
16

julia> get_width(TERMINUS_16_8)
8
```
