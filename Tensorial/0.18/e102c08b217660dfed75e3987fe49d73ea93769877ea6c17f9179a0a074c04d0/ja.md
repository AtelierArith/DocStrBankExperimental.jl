```
contract(x, y, Val(xdims), Val(ydims))
```

指定された次元での収縮を実行します。

# 例

```jldoctest
julia> A = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.325977  0.894245  0.953125
 0.549051  0.353112  0.795547
 0.218587  0.394255  0.49425

julia> B = rand(Mat{3,3})
3×3 Tensor{Tuple{3, 3}, Float64, 2, 9}:
 0.748415  0.00744801  0.682533
 0.578232  0.199377    0.956741
 0.727935  0.439243    0.647855

julia> contract(A, B, Val(1), Val(2)) ≈ @einsum A[k,i] * B[j,k]
true

julia> contract(A, B, Val((1,2)), Val((2,1))) ≈ @einsum A[i,j] * B[j,i]
true
```
