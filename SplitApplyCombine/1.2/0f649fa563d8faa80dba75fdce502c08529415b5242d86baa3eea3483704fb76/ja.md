```
flatten(a)
```

コレクションのコレクション `a` を受け取り、`a` のサブコレクションのすべての要素を含むコレクションを返します。`mapmany(idenity, a)` と同等です。

# 例

```jldoctest
julia> flatten([1:1, 1:2, 1:3])
6-element Array{Int64,1}:
 1
 1
 2
 1
 2
 3
```
