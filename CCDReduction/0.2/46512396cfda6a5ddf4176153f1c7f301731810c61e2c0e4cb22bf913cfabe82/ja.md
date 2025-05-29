```
crop(frame, shape; force_equal = true, [hdu = 1])
```

`frame`を`shape`で指定されたサイズに、フレームの中心を基準にして切り取ります。

これにより、`frame`の行/列が両側で均等に削除されます。サイズに不均等な差がある場合（例：サイズ9 -> 6は均等に削除できない）、デフォルトでは出力サイズを増やします（例：6 -> 7）ので、両側で均等に削除されます。これを無効にするには、`force_equal=false`を設定すると、軸の端から余分なスライスが削除されます。

`frame`が文字列の場合、最初に[`CCDData`](@ref)に読み込まれます。読み込まれるHDUは、デフォルトで1の`hdu`で指定できます。

# 例

```jldoctest
julia> frame = reshape(1:25, (5, 5));

julia> crop(frame, (3, 3))
3×3 Matrix{Int64}:
 7  12  17
 8  13  18
 9  14  19

julia> crop(frame, (4, 3), force_equal = false)
4×3 Matrix{Int64}:
 6  11  16
 7  12  17
 8  13  18
 9  14  19
```

# 参照

[`cropview`](@ref)
