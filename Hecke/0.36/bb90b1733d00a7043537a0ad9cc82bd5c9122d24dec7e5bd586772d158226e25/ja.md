```
cyclotomic_units_totally_real(K::NumField)
```

与えられた素数導関数のサイクロトミック体の最大の完全実部分体 $K$ に対して、$K$ のサイクロトミック単位の生成集合を返します。

# 例

```jldoctest
julia> K, a = cyclotomic_real_subfield(7);

julia> cyclotomic_units_totally_real(K)
3-element Vector{AbsSimpleNumFieldElem}:
 -1
 (z_7 + 1/z_7)^2 - 1
 -(z_7 + 1/z_7)^2 - (z_7 + 1/z_7) + 2
```
