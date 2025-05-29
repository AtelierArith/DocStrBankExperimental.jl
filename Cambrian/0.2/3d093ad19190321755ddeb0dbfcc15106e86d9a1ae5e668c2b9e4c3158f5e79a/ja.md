```julia
# Dictを名前付きタプルに変換する
function dict_to_named_tuple(d::Dict)
    return NamedTuple(d)
end
```
