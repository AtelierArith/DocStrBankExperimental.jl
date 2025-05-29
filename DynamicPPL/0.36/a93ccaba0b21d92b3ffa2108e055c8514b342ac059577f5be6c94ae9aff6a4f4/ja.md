```
values_as(vnv::VarNamedVector[, T])
```

`vnv`の値/実現を型`T`として返します（実装されている場合）。

型`T`が提供されていない場合、`vnv`に格納されている値をそのまま返します。

# 例

```jldoctest
julia> using DynamicPPL: VarNamedVector

julia> vnv = VarNamedVector(@varname(x) => 1, @varname(y) => [2.0]);

julia> values_as(vnv) == [1.0, 2.0]
true

julia> values_as(vnv, Vector{Float32}) == Vector{Float32}([1.0, 2.0])
true

julia> values_as(vnv, OrderedDict) == OrderedDict(@varname(x) => 1.0, @varname(y) => [2.0])
true

julia> values_as(vnv, NamedTuple) == (x = 1.0, y = [2.0])
true
```
