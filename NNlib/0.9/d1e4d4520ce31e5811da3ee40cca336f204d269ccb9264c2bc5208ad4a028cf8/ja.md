```
upsample_nearest(x, scale::NTuple{S,Int})
upsample_nearest(x; size::NTuple{S,Int})
```

配列 `x` を最初の `S` 次元に沿って整数倍にアップサンプリングします。`x` の後続の次元は変更されません。

`scale` 要因または最終出力 `size` のいずれかを指定できます。

他に [`upsample_bilinear`](@ref) を参照してください。これは `N=4` の配列の2次元に関するものです。

# 例

```jldoctest
julia> upsample_nearest([1 2 3; 4 5 6], (2, 3))
4×9 Matrix{Int64}:
 1  1  1  2  2  2  3  3  3
 1  1  1  2  2  2  3  3  3
 4  4  4  5  5  5  6  6  6
 4  4  4  5  5  5  6  6  6

julia> ans == upsample_nearest([1 2 3; 4 5 6]; size=(4, 9))  # 同等
true

julia> upsample_nearest([1 2 3; 4 5 6], (2,))
4×3 Matrix{Int64}:
 1  2  3
 1  2  3
 4  5  6
 4  5  6

julia> ans == upsample_nearest([1 2 3; 4 5 6], size=(4,))
true
```
