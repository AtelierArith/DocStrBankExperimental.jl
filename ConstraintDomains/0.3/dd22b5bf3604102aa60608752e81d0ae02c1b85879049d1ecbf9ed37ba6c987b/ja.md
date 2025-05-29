```
domain(values)
domain(range::R) where {T <: Real, R <: AbstractRange{T}}
```

`SetDomain` または `RangeDomain` のいずれかを構築します。

```julia
d1 = domain(1:5)
d2 = domain([53.69, 89.2, 0.12])
d3 = domain([2//3, 89//123])
d4 = domain(4.3)
d5 = domain(1,42,86.9)
```
