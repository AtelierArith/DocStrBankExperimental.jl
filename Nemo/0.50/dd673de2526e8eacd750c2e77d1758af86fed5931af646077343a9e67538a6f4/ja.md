```
number_of_partitions(x::Int)
number_of_partitions(x::ZZRingElem)
```

$$
x
$$

の分割数を返します。

# 例

```jldoctest
julia> number_of_partitions(100)
190569292

julia> number_of_partitions(ZZ(1000))
24061467864032622473692149727991
```
