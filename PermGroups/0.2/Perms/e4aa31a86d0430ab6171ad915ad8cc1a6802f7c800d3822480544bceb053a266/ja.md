`mappingPerm([::Type{T},]a,b)`

与えられた重複のない正の整数のリスト `a` と `b` に対して、この関数は `a.^p==b` となる `Perm{T}` `p` を見つけます。省略された場合、`T` は `Int16` として取られます。

```julia-repl
julia> mappingPerm([1,2,5,3],[2,3,4,6])
(1,2,3,6,5,4)
```
