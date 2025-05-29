```
gray_scale_image(
    [T=Float32];
    rows=40,
    cols=200,
    swidth=nothing,
    sheight=nothing,
    gray_scale=-1000..1000,
) where {T}
```

指定されたスケール gray_scale を持つグレースケールの長方形を持つ画像を作成します。

# 例

```julia-repl
julia> gray_scale_image(swidth=80, sheight=40, gray_scale=-1000..1000)
40×80 Array{Float32,2}:
[...]
```

参照: [`circle_image`](@ref), [`combine_images`](@ref)
