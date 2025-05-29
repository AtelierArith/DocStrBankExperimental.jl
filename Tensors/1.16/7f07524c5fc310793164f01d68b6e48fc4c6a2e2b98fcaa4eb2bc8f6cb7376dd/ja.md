```
transpose(::Vec)
transpose(::SecondOrderTensor)
transpose(::FourthOrderTensor)
```

テンソルの転置を計算します。4次のテンソルの場合、転置は小さな転置です。

# 例

```jldoctest
julia> A = rand(Tensor{2,2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> A'
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.549051
 0.218587  0.894245
```
