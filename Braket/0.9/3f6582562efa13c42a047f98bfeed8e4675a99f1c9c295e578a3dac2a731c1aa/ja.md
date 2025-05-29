```
qubit_count(c::Circuit) -> Int
```

`c`が定義されているキュービットの数を返します。

# 例

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> qubit_count(c)
2
```
