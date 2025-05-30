```
==(a::AbstractString, b::AbstractString) -> Bool
```

2つの文字列が文字ごとに等しいかどうかをテストします（技術的には、Unicode コードポイントごとに）。

# 例

```jldoctest
julia> "abc" == "abc"
true

julia> "abc" == "αβγ"
false
```
