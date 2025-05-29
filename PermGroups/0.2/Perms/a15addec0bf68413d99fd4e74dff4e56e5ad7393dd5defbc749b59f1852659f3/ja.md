`mappingPerm([::Type{T},]a::AbstractVector{<:Integer})`

正の整数のリスト `a`（重複なし）を与えると、この関数は `sort(a).^p==a` となる `Perm{T}` `p` を見つけます。これは、配置と `Perm` の間の変換に使用できます。省略された場合、`T` は `Int16` として取られます。

```julia-repl
julia> p=mappingPerm([6,7,5])
(5,6,7)

julia> (5:7).^p
3-element Vector{Int64}:
 6
 7
 5
```
