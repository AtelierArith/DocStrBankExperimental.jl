```
number_of_digits(x::ZZRingElem, b::Integer)
```

$$
x
$$

の基数$b$における桁数を返します（デフォルトは$b = 10$）。

# 例

```jldoctest
julia> number_of_digits(ZZ(12), 3)
3
```
