```
angle(z)
```

複素数 `z` の位相角をラジアンで計算します。

関連情報: [`atan`](@ref), [`cis`](@ref).

# 例

```jldoctest
julia> rad2deg(angle(1 + im))
45.0

julia> rad2deg(angle(1 - im))
-45.0

julia> rad2deg(angle(-1 - im))
-135.0
```
