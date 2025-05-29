```
iter(x::Option)::OptionIterator
```

`x` に対してイテレータを生成します。`x` が `some` の場合はその結果値を返し、`none` の場合は空のイテレータを返します。

# 例

```
julia> first(iter(some(19)))
19

julia> collect(iter(some("some string")))
1-element Vector{String}:
 "some string"

julia> isempty(iter(none(Dict)))
true

julia> collect(iter(none(Char)))
Char[]
```
