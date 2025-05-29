```
nbits(x::ZZRingElem)
```

$$
x
$$

の2進数ビット数を返します。$x = 0$の場合はゼロを返します。

# 例

```jldoctest
julia> nbits(ZZ(12))
4
```
