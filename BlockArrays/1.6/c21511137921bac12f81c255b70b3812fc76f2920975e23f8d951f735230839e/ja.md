```
BlockedArray{T, N, R} <: AbstractBlockArray{T, N}
```

`BlockedArray`は[`BlockArray`](@ref)に似ていますが、全体の配列がブロックごとではなく連続して格納されます。これは、データをコピーせずにブロックを挿入したり取得したりすることができないことを意味します。一方、`BlockedArray`の`parent`は、ラップされた配列を返すだけなので即座に実行されます。

勾配法を用いて一連の方程式を反復的に解く際、ヤコビ行列は通常ブロック構造を持っています。ヤコビ行列をブロックごとに構築するために`BlockedArray`を使用し、その後、`parent`を使用して得られた行列を直接ソルバーに渡すことが便利です。

# 例

```jldoctest
julia> A = zeros(Int, 2, 3);

julia> B = BlockedArray(A, [1,1], [2,1])
2×2-blocked 2×3 BlockedMatrix{Int64}:
 0  0  │  0
 ──────┼───
 0  0  │  0

julia> parent(B) === A
true

julia> B[Block(1,1)] .= 4
1×2 view(::Matrix{Int64}, 1:1, 1:2) with eltype Int64:
 4  4

julia> A
2×3 Matrix{Int64}:
 4  4  0
 0  0  0
```
