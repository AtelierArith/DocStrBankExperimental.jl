```
dev(::SecondOrderTensor)
```

二次テンソルの偏差部分を計算します。

# 例

```jldoctest
julia> A = rand(Tensor{2, 3});

julia> dev(A)
3×3 Tensor{2, 3, Float64, 9}:
 -0.065136   0.894245   0.953125
  0.549051  -0.0380011  0.795547
  0.218587   0.394255   0.103137

julia> tr(dev(A))
5.551115123125783e-17
```
