'reorder(U,l[,order])'

この関数は、単位元を表すペアのリスト 'r=>c' を受け取り、'r' が根で 'c' が対応する係数である場合、標準形に配置し、項を 'U.order' に従って再配置します。第二引数が与えられた場合、これは 'U.order' の代わりに使用されます。

```julia-repl
julia> U=UnipotentGroup(coxgroup(:G,2))
UnipotentGroup(G₂)

julia> l=reorder(U,[2=>4,1=>2])
6-element Vector{Pair{Int64, Int64}}:
 1 => 2
 2 => 4
 3 => -8
 4 => 32
 5 => -128
 6 => 512

julia> reorder(U,l,6:-1:1)
2-element Vector{Pair{Int64, Int64}}:
 2 => 4
 1 => 2
```
