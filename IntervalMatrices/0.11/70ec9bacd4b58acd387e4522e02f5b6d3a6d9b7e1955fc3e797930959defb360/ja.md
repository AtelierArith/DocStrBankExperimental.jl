```
IntervalMatrix(A::MT, B::MT) where {T, MT<:AbstractMatrix{T}}
```

下限と上限の境界がそれぞれ行列 `A` と `B` によって与えられる区間行列を返します。

### 入力

  * `A` – 下限行列
  * `B` – 上限行列

### 出力

区間行列 `M` を返します。ここで `M[i, j]` は下限が `A[i, j]` で上限が `B[i, j]` である区間に対応します。すなわち、$M_{ij} = [A_{ij}, B_{ij}]$ です。

### 注意事項

上限は下限以上でなければなりません。すなわち、各 `i` と `j` に対して `B[i, j] ≥ A[i, j]` です。

### 例

```jldoctest
julia> IntervalMatrix([1 2; 3 4], [1 2; 4 5])
2×2 IntervalMatrix{Float64, Interval{Float64}, Matrix{Interval{Float64}}}:
 [1.0, 1.0]  [2.0, 2.0]
 [3.0, 4.0]  [4.0, 5.0]
```
