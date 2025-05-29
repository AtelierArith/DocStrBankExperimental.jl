```
dev(::AbstractSecondOrderTensor{3})
dev(::AbstractSymmetricSecondOrderTensor{3})
```

正方テンソルの偏差部分を計算します。これは3Dでのみ利用可能です。

# 例

```jldoctest
julia> x = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> dev(x)
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 -0.065136   0.894245   0.953125
  0.549051  -0.0380011  0.795547
  0.218587   0.394255   0.103137

julia> tr(dev(x))
5.551115123125783e-17
```
