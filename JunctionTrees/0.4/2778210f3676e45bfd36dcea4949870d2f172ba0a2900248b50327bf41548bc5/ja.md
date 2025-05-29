```julia
norm(A::JunctionTrees.Factor{T, N}) -> JunctionTrees.Factor

```

ファクター A の値を正規化して合計が 1 になるようにします。

# 例

```jldoctest
A = Factor{Float64,2}((1, 2), [0.2 0.4; 0.6 0.8])
norm(A)

# 出力

Factor{Float64, 2}((1, 2), [0.1 0.2; 0.3 0.4])
```
