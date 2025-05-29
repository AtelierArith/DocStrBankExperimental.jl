```
is_strongly_regular(A::AbstractMatrix{T}) where {T<:Interval}
```

平方区間行列 $A$ が強正則であるかどうかをテストします。すなわち、$A_c^{-1}A$ が H-行列であるかどうかを確認します。ここで、$A_c$ は $A$ の中点行列です。詳細については、[[HOR19]](@ref) のセクション 4.6 を参照してください。

### 例

```jldoctest
julia> A = [2..4 -2..1; -1..2 2..4]
2×2 Matrix{Interval{Float64}}:
  [2, 4]  [-2, 1]
 [-1, 2]   [2, 4]

julia> is_strongly_regular(A)
true

julia> A = [0..2 1..1;-1.. -1 0..2]
2×2 Matrix{Interval{Float64}}:
   [0, 2]  [1, 1]
 [-1, -1]  [0, 2]

julia> is_strongly_regular(A)
false
```
