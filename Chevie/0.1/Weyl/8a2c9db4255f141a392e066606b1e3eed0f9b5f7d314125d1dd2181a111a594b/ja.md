`with_inversions(W,N)`

`W` は有限コクセター群であり、`N` は `1:nref(W)` の部分集合であるべきです。`N==inversions(W,w)` となる `W` の要素 `w` を返します。そのような要素が存在しない場合は `nothing` を返します。

```julia-repl
julia> W=coxgroup(:A,2)
A₂

julia> map(N->with_inversions(W,N),combinations(1:nref(W)))
8-element Vector{Union{Nothing, Perm{Int16}}}:
 ()
 (1,4)(2,3)(5,6)
 (1,3)(2,5)(4,6)
 nothing
 nothing
 (1,6,2)(3,5,4)
 (1,2,6)(3,4,5)
 (1,5)(2,4)(3,6)
```
