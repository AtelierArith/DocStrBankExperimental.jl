```
filter(f, a)
```

コレクション `a` のコピーを返し、`f` が `false` の要素を削除します。関数 `f` には1つの引数が渡されます。

!!! compat "Julia 1.4"
    `a` をタプルとしてサポートするには、少なくとも Julia 1.4 が必要です。


関連情報: [`filter!`](@ref), [`Iterators.filter`](@ref).

# 例

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
