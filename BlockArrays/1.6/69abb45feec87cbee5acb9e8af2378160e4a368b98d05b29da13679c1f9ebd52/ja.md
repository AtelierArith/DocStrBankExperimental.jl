```
mortar(blocks::AbstractArray)
mortar(blocks::AbstractArray{R, N}, sizes_1, sizes_2, ..., sizes_N)
mortar(blocks::AbstractArray{R, N}, block_sizes::Tuple{Vararg{AbstractUnitRange{<:Integer},N}})
```

`blocks`から`BlockArray`を構築します。`block_sizes`は、指定されていない場合、`blocks`から計算されます。

これは[`blocks`](@ref)の「逆」です。

# 例

```jldoctest
julia> arrays = permutedims(reshape([
                  fill(1.0, 1, 3), fill(2.0, 1, 2),
                  fill(3.0, 2, 3), fill(4.0, 2, 2),
              ], (2, 2)))
2×2 Matrix{Matrix{Float64}}:
 [1.0 1.0 1.0]               [2.0 2.0]
 [3.0 3.0 3.0; 3.0 3.0 3.0]  [4.0 4.0; 4.0 4.0]

julia> M = mortar(arrays)
2×2-blocked 3×5 BlockMatrix{Float64}:
 1.0  1.0  1.0  │  2.0  2.0
 ───────────────┼──────────
 3.0  3.0  3.0  │  4.0  4.0
 3.0  3.0  3.0  │  4.0  4.0

julia> M == mortar(
                  (fill(1.0, 1, 3), fill(2.0, 1, 2)),
                  (fill(3.0, 2, 3), fill(4.0, 2, 2)),
              )
true
```
