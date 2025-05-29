```
namedtuple(  name1, name2, ..  )
namedtuple( (name1, name2, ..) )
namedtuple(  namedtuple )
```

フィールド名を指定または取得することによって NamedTuple プロトタイプを生成します。プロトタイプはフィールド値に適用され、完成した NamedTuple を生成します。

# 例

julia> ntprototype = namedtuple( :a, :b, :c )

NamedTuple{(:a, :b, :c),T} where T<:Tuple

julia> nt123 = ntprototype(1, 2, 3)

(a = 1, b = 2, c = 3)

julia> ntAb3 = ntprototype("A", "b", 3)

(a = "A", b = "b", c = 3)

see: [`isprototype`](@ref)
