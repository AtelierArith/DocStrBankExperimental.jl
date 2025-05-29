`orbits(gens::Vector,v,action=^;trivial=true)`

`orbits(G,v,action=^;trivial=true)`

`gens`の繰り返し作用の`v`上の軌道；`v`の要素はハッシュ可能である必要があります。生成子の代わりに群が与えられた場合、`gens(G)`の下の軌道が返されます。`trivial=false`の場合、1要素の軌道は返されません。

```julia-repl
julia> G=Group(Perm(1,2),Perm(2,3));
julia> orbits(G,1:4)
2-element Vector{Vector{Int64}}:
 [1, 2, 3]
 [4]
```
