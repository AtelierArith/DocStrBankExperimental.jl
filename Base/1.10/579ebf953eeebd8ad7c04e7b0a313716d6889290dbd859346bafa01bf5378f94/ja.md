```
findprev(predicate::Function, A, i)
```

`predicate` が `true` を返す `A` の要素の、`i` の前または `i` を含む前のインデックスを見つけます。見つからない場合は `nothing` を返します。

インデックスは [`keys(A)`](@ref) および [`pairs(A)`](@ref) によって返されるものと同じ型です。

# 例

```jldoctest
julia> A = [4, 6, 1, 2]
4-element Vector{Int64}:
 4
 6
 1
 2

julia> findprev(isodd, A, 1) # 何も返さないが、REPL には表示されない

julia> findprev(isodd, A, 3)
3

julia> A = [4 6; 1 2]
2×2 Matrix{Int64}:
 4  6
 1  2

julia> findprev(isodd, A, CartesianIndex(1, 2))
CartesianIndex(2, 1)
```
