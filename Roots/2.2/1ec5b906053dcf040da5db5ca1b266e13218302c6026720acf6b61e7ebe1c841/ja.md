```
AllZeros
```

`solve` に `find_zeros` を使用して与えられた `ZeroProblem` を解くことを示すためのタイプです。

## 例

```
julia> Z = ZeroProblem(cos, (0, 2pi));

julia> solve(Z, AllZeros())
2-element Vector{Float64}:
 1.5707963267948966
 4.71238898038469
```
