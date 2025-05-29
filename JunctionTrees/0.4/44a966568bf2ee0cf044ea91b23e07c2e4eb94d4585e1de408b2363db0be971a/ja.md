```julia
sum(
    A::JunctionTrees.Factor{T, ND},
    V::NTuple{N, Int64} where N
) -> JunctionTrees.Factor

```

変数 `V` を因子 A から合計します。

# 例

```jldoctest
A = Factor{Float64,2}((1, 2), [0.59 0.41; 0.22 0.78])
sum(A, (2,))

# 出力

Factor{Float64, 1}((1,), [1.0, 1.0])
```
