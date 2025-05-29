```
IdentityRange(start, stop) -> idr
IdentityRange(r::AbstractUnitRange) -> idr
```

`idr[i] == i` となる `AbstractUnitRange` を定義します。これは、任意の有効な `i` に対して成り立ちます。あるいは、`axes(idr, 1)` は `idr` に存在するのと同じ値を持つ範囲を返します。

これは、提供された軸を保持する配列の `view` を作成するのに特に便利です：

```jldoctest
julia> a = rand(8);

julia> v1 = view(a, 3:5);

julia> axes(v1, 1)
Base.OneTo(3)

julia> idr = IdentityRange(3:5)
IdentityRange(3:5)

julia> v2 = view(a, idr);

julia> axes(v2, 1)
3:5
```
