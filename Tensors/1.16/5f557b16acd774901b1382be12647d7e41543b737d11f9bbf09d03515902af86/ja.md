```
tdot(A::SecondOrderTensor)
```

`A`の転置ドット積、すなわち`dot(A', A)`を計算します。`SymmetricTensor`を返します。

# 例

```jldoctest
julia> A = rand(Tensor{2,3})
3×3 Tensor{2, 3, Float64, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> tdot(A)
3×3 SymmetricTensor{2, 3, Float64, 6}:
 0.455498  0.571559  0.855529
 0.571559  1.0798    1.3281
 0.855529  1.3281    1.78562
```
