```
orderof(x::FiniteStrainParameters)
```

`FiniteStrainParameters`の順序を返します。

# 例

```jldoctest
julia> orderof(BirchMurnaghan(40, 0.5, 4, 0)) == 3
true
```
