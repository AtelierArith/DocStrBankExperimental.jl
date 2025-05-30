```
isempty(collection) -> Bool
```

コレクションが空であるかどうかを判断します（要素がない）。

!!! warning
    `isempty(itr)` は、適切な `Base.isdone(itr)` または `isempty` メソッドが定義されていない限り、状態を持つイテレータ `itr` の次の要素を消費する可能性があります。したがって、任意のイテレータタイプをサポートする一般的なコードを書く際には `isempty` の使用を避けるべきです。


# 例

```jldoctest
julia> isempty([])
true

julia> isempty([1 2 3])
false
```
