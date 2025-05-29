```
depth(c::Circuit)
```

`c`のモーメントの数を返します。これは「並列ゲートの深さ」とも呼ばれます。

# 例

```jldoctest
julia> c = Circuit();

julia> H(c, 0);

julia> CNot(c, 0, 1);

julia> depth(c)
2
```
