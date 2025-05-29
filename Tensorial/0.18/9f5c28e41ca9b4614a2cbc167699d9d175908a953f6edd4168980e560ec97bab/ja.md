```
skew(A)
```

2次テンソルの歪対称（反対称）部分を計算します。

# 例

```jldoctest
julia> x = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> symmetric(x) + skew(x) ≈ x
true
```
