```
hex(n::ZZRingElem) = base(n, 16)
```

$$
n
$$

を16進数の文字列として返します。

# 例

```jldoctest
julia> hex(ZZ(12))
"c"
```
