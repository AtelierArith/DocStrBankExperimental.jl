```
constants(f = 𝒾, xs)
```

`map(x -> @atomize $(f(x)), xs)` と同等です。

関連項目は [`identical`](@ref) です。

# 例

```jldoctest
julia> constants(1:2)
2-element Vector{PAndQ.Constant}:
 $(1)
 $(2)

julia> constants(string, 1:2)
2-element Vector{PAndQ.Constant}:
 $("1")
 $("2")
```
