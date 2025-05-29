```
subtract_bias(frame, bias_frame; [hdu = 1])
```

`bias_frame`を`frame`から引き算します。

どちらかが文字列の場合、最初に[`CCDData`](@ref)に読み込まれます。読み込まれるHDUは、整数または各ファイルに対応するタプルとして`hdu`で指定できます。

# 例

```jldoctest
julia> frame = [1.0 2.2 3.3 4.5];

julia> bias = [0.0 0.2 0.3 0.5];

julia> subtract_bias(frame, bias)
1×4 Matrix{Float64}:
 1.0  2.0  3.0  4.0

```

# 参照

[`subtract_bias!`](@ref)
