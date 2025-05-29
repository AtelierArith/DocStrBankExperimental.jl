```
searchsortedat(coll, x)
```

ソートされたコレクション `coll` の中で、`x` に最も近い要素のインデックスを返します。`coll` がソートされていない場合、`searchsortedat` は静かに間違った結果を返す可能性があります。

```jldoctest
julia> using RangeHelpers

julia> searchsortedat(100:100:1000, around(200))
2

julia> searchsortedat(100:100:1000, around(249))
2

julia> searchsortedat(100:100:1000, around(251))
3

julia> searchsortedat(100:100:1000, below(251))
2

julia> searchsortedat(100:100:1000, above(249))
3

julia> searchsortedat(100:100:1000, 300)
3

julia> searchsortedat(100:100:1000, 301)
ERROR: ArgumentError: coll does not contain x:
coll = 100:100:1000
x = 301
Try `searchsortedat(coll, around(x))`
```
