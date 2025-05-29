```
@reset assignment
```

`obj = @set obj...` のショートカットです。

# 例

```jldoctest
julia> using Accessors

julia> t = (a=1,)
(a = 1,)

julia> @reset t.a=2
(a = 2,)

julia> t
(a = 2,)
```

[`@optic`](@ref) と同じ構文をサポートしています。詳細は [`@set`](@ref) を参照してください。
