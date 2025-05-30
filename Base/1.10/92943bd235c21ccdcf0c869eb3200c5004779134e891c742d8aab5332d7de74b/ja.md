```
argmax(itr)
```

コレクション内の最大要素のインデックスまたはキーを返します。最大要素が複数ある場合は、最初のものが返されます。

コレクションは空であってはいけません。

値は `isless` で比較されます。

関連項目: [`argmin`](@ref), [`findmax`](@ref).

# 例

```jldoctest
julia> argmax([8, 0.1, -9, pi])
1

julia> argmax([1, 7, 7, 6])
2

julia> argmax([1, 7, 7, NaN])
4
```
