```
symmetric(::SecondOrderTensor)
symmetric(::FourthOrderTensor)
```

第二または第四階テンソルの（小）対称部分を計算します。`SymmetricTensor`を返します。

# 例

```jldoctest
julia> A = rand(Tensor{2,2})
2×2 Tensor{2, 2, Float64, 4}:
 0.325977  0.218587
 0.549051  0.894245

julia> symmetric(A)
2×2 SymmetricTensor{2, 2, Float64, 3}:
 0.325977  0.383819
 0.383819  0.894245
```
