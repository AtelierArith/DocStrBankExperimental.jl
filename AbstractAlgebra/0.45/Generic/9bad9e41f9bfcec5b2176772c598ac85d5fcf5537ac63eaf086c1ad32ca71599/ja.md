```
size(Y::YoungTableau)
```

`Y`を含む最小の配列の`size`、すなわち`Y`の行数と列数のタプルを返します。

# 例

```jldoctest
julia> y = YoungTableau([4,3,1]); size(y)
(3, 4)
```
