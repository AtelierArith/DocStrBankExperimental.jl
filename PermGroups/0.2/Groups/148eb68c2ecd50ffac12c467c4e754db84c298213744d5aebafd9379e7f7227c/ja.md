`orbit(gens::AbstractVector,p,action::Function=^)`

`orbit(G::Group,p,action::Function=^)`

点 `p` の軌道は、生成子 `gens` の繰り返し作用の下でのものです。点 `p` の型はハッシュ可能である必要があります。群の要素のデフォルトの作用は `^` です。例えば、`g` が置換で `p` が整数の場合、`p^g` は `g` による `p` の像です。もし `h` と `g` が群の要素であれば、`h^g` は共役 `inv(g)*h*g` です。生成子の代わりに群が与えられた場合、`gens(G)` の下での軌道が返されます。

```julia-repl
julia> orbit([Perm(1,2),Perm(2,3)],1)
3-element Vector{Int64}:
 1
 2
 3

julia> orbit([Perm(1,2),Perm(2,3)],[1,3],ontuples)
6-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 3]
 [1, 2]
 [3, 2]
 [2, 1]
 [3, 1]

julia> orbit([Perm(1,2),Perm(2,3)],[1,3],(v,g)->sort(v.^g)) # "OnSets"
3-element Vector{Vector{Int64}}:
 [1, 3]
 [2, 3]
 [1, 2]
```
