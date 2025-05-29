`Perm{T}(l::AbstractVector,l1::AbstractVector)`

は、`invpermute(l1,p)==l` となる `p`、すなわち `Perm{T}` を返します。もしそのような `p` が存在しない場合は `nothing` を返します。 `{T}` が指定されていない場合は `{Int16}` が使用されます。`l` と `l1` の `eltype` はソート可能である必要があります。

```julia-repl
julia> Perm([0,2,4],[4,0,2])
(1,3,2)
```
