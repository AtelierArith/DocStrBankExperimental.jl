```
rpad_constant(v::AbstractArray, n::Union{Integer, Tuple}, val = 0; dims=:)
```

指定された次元 `dims` に沿って、最大長さ `n` まで `val` でパディングされたシーケンスを返します。

# 例

```jldoctest
julia> rpad_constant([1, 2], 4, -1) # サイズ4まで-1でパディング
4-element Vector{Int64}:
  1
  2
 -1
 -1

julia> rpad_constant([1, 2, 3], 2) # 長さがすでにnより大きい場合はパディングなし
3-element Vector{Int64}:
 1
 2
 3

julia> rpad_constant([1 2; 3 4], 4; dims=1) # 最初の次元に沿ってパディング
4×2 Matrix{Int64}:
 1  2
 3  4
 0  0
 0  0

julia> rpad_constant([1 2; 3 4], 4) # デフォルトで全ての次元に沿ってパディング
4×4 Matrix{Int64}:
 1  2  0  0
 3  4  0  0
 0  0  0  0
 0  0  0  0
```
