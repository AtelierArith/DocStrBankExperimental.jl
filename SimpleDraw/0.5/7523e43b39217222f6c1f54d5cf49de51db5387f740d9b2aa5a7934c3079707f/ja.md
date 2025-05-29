```
get_height(font::MonospaceBitmapASCIIFont)
```

モノスペースフォント `font` に含まれるグリフの高さを i 軸（垂直軸、1 番目の軸）に沿って返します。

[`get_width`](@ref) も参照してください。

# 例

```julia-repl
julia> get_height(TERMINUS_32_16)
32

julia> get_height(TERMINUS_16_8)
16
```
