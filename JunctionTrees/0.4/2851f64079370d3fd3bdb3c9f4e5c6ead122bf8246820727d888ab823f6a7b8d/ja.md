```julia
prod(
    A::JunctionTrees.Factor{T},
    B::JunctionTrees.Factor{T}
) -> JunctionTrees.Factor

```

テーブル `A` と `B` の因子積を計算します。

# 例

```jldoctest
A = Factor{Float64,2}((2, 3), [0.5 0.7; 0.1 0.2])
B = Factor{Float64,2}((1, 2), [0.5 0.8; 0.1 0.0; 0.3 0.9])
prod(A, B)

# 出力

Factor{Float64, 3}((1, 2, 3), [0.25 0.08000000000000002; 0.05 0.0; 0.15 0.09000000000000001;;; 0.35 0.16000000000000003; 0.06999999999999999 0.0; 0.21 0.18000000000000002])
```
