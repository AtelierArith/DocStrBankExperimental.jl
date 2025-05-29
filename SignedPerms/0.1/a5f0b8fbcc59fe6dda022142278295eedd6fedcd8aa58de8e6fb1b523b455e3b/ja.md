`SPerm{T}(l::AbstractVector,l1::AbstractVector)`

`invpermute(l1,p)==l` となる `SPerm{T}` `p` を返します。もしそのような `p` が存在しない場合は、何も返しません。 `{T}` が指定されていない場合は、 `{Int16}` が使用されます。 `l` と `l1` のエントリはソート可能であり、`-` 演算が必要です。

```julia-repl
julia> p=SPerm([20,30,40],[-40,-20,-30])
(1,-3,2,-1,3,-2)

julia> invpermute([-40,-20,-30],p)
3-element Vector{Int64}:
 20
 30
 40
```
