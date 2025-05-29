```
subtract_overscan(frame, idxs; dims = axes_min_length(idxs), [hdu = 1])
```

画像からオーバースキャンフレームを引きます。

`dims` は `overscan_frame` が結合される次元です。`dims` のデフォルト値はオーバースキャン領域内の長さが小さい軸です。`idxs` が文字列の場合、FITSスタイルのインデックスとして解析されます。

`frame` が文字列の場合、最初に [`CCDData`](@ref) に読み込まれます。読み込まれるHDUはデフォルトで1の `hdu` によって指定できます。

# 例

```jldoctest
julia> frame = [4.0 2.0 3.0 1.0 1.0];

julia> subtract_overscan(frame, (:, 4:5), dims = 2)
1×5 Matrix{Float64}:
 3.0  1.0  2.0  0.0  0.0

julia> subtract_overscan(frame, "[4:5, 1:1]", dims = 2)
1×5 Matrix{Float64}:
 3.0  1.0  2.0  0.0  0.0
```

# 参照

[`subtract_overscan!`](@ref) ```
