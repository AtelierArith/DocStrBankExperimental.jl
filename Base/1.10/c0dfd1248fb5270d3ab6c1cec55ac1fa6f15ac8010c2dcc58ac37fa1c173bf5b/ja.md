```
findmax(itr) -> (x, index)
```

コレクション `itr` の最大要素とそのインデックスまたはキーを返します。最大要素が複数ある場合は、最初のものが返されます。値は `isless` で比較されます。

参照: [`findmin`](@ref), [`argmax`](@ref), [`maximum`](@ref).

# 例

```jldoctest
julia> findmax([8, 0.1, -9, pi])
(8.0, 1)

julia> findmax([1, 7, 7, 6])
(7, 2)

julia> findmax([1, 7, 7, NaN])
(NaN, 4)
```
