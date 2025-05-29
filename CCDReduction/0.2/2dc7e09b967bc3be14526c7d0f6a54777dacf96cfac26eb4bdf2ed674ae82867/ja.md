```
subtract_dark(frame, dark_frame; data_exposure = 1, dark_exposure = 1, [hdu = 1])
```

`dark_frame`を`frame`から引き算します。

どちらかが文字列の場合、最初に[`CCDData`](@ref)に読み込まれます。読み込まれるHDUは、整数または各ファイルに対応するタプルとして`hdu`で指定できます。

# 例

```jldoctest
julia> frame = ones(3, 3);

julia> dark_frame = ones(3, 3);

julia> subtract_dark(frame, dark_frame)
3×3 Matrix{Float64}:
 0.0  0.0  0.0
 0.0  0.0  0.0
 0.0  0.0  0.0

julia> subtract_dark(frame, dark_frame, data_exposure = 1, dark_exposure = 4)
3×3 Matrix{Float64}:
 0.75  0.75  0.75
 0.75  0.75  0.75
 0.75  0.75  0.75

```

# 参照

[`subtract_dark!`](@ref)
