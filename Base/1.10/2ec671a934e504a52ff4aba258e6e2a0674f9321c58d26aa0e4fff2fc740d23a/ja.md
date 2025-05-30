```
argmin(itr)
```

コレクション内の最小要素のインデックスまたはキーを返します。最小要素が複数ある場合は、最初のものが返されます。

コレクションは空であってはいけません。

`NaN`は、`missing`を除くすべての値よりも小さいと見なされます。

関連情報: [`argmax`](@ref), [`findmin`](@ref).

# 例

```jldoctest
julia> argmin([8, 0.1, -9, pi])
3

julia> argmin([7, 1, 1, 6])
2

julia> argmin([7, 1, 1, NaN])
4
```
