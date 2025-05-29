```
Limit{T}(x, s)
```

Limit型は閉区間と開区間の端点を表します。valフィールドは端点の値です。signフィールドは、無限小を使用して区間端点の開放性/閉鎖性を表すために使用されます。

```jl-doctest julia> limit(1.0) 1.0+0

julia> plus_eps(1.0) 1.0+ϵ

julia> minus_eps(1.0) 1.0-ϵ

julia> plus*eps(1.0) + minus*eps(1.0) 2.0+0.0

julia> plus_eps(1.0) * 2 2.0+2.0ϵ

julia> plus*eps(1.0) * minus*eps(1.0) 1.0-1.0ϵ

julia> plus*eps(-1.0) * minus*eps(1.0) -1.0+2.0ϵ

julia> 1.0 < plus_eps(1.0) true

julia> 1.0 < minus_eps(1.0) false
```
