`partitions(n::Integer,set::AbstractVector[,k])`, `npartitions(n::Integer,set::AbstractVector[,k])`   

は、`n` の分割のリストを返します（`k` が与えられた場合は `k` 部分に制限され、`set` に含まれる部分を持つ）。`npartitions` はそのような分割の数を（より速く）提供します。

2、5、10セントのコインを使って17セントを支払う方法がいくつあるかを示しましょう。

```julia-repl
julia> npartitions(17,[10,5,2])
3

julia> partitions(17,[10,5,2])
3-element Vector{Vector{Int64}}:
 [5, 2, 2, 2, 2, 2, 2]
 [5, 5, 5, 2]
 [10, 5, 2]

julia> npartitions(17,[10,5,2],3) # 3枚のコインで支払う
1

julia> partitions(17,[10,5,2],3) 
1-element Vector{Vector{Int64}}:
 [10, 5, 2]
```
