`cycletype(a::Perm,domain::AbstractVector{<:Integer};trivial=true)`

`domain` は `a` の軌道の和であるべきです。`domain` の対称群における `a` の共役類に関連する `length(domain)` の分割を返します。`trivial=false` の場合は1が削除されます（この場合、分割は `domain` には依存せず、単に `support(a)` のみに依存します）。

`cycletype(a::Perm)`

`cycletype(a,1:last_moved(a);trivial=false)` を返します。

# 例

```julia-repl
julia> cycletype(Perm(1,2)*Perm(4,5))
2-element Vector{Int64}:
 2
 2

julia> cycletype(Perm(1,2)*Perm(4,5),1:5)
3-element Vector{Int64}:
 2
 2
 1

julia> cycletype(Perm(1,2)*Perm(4,5),1:6)
4-element Vector{Int64}:
 2
 2
 1
 1
```
