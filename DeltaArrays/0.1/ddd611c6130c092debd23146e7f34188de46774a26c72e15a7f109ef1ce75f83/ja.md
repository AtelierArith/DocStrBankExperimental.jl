```
DeltaArray(M::AbstractMatrix)
```

`M`の対角線から行列を構築します。

# 注意

結果の`DeltaArray`は`Diagonal`オブジェクトと同様の方法であるべきです。

# 例

```jldoctest julia> A = permutedims(reshape(1:15, 5, 3)) 3×5 Matrix{Int64}:   1   2   3   4   5   6   7   8   9  10  11  12  13  14  15

julia> DeltaArray(A) 3×3 DeltaArray{Int64, 2, Vector{Int64}}:  1  0   0  0  7   0  0  0  13

julia> delta(A) 3-element Vector{Int64}:   1   7  13
```
