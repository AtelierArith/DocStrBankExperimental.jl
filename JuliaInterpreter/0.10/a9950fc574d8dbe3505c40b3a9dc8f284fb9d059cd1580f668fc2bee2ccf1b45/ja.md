```
@interpret [interp] f(args; kwargs...)
```

指定された引数を使用してインタプリタで `f` を評価します。

# 例

```jldoctest
julia> a = [1, 7];

julia> sum(a)
8

julia> @interpret sum(a)
8
```
