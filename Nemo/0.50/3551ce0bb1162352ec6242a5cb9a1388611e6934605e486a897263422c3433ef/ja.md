```
base(n::ZZRingElem, b::Integer)
```

$$
2 \leq b \leq 62
$$

の範囲で、$n$ を基数 $b$ の文字列として返します。

# 例

```jldoctest
julia> base(ZZ(12), 13)
"c"
```
