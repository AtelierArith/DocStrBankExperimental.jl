```
normalize(x::Decimal)
```

等しい数をその最も単純な形に減らし、係数の末尾のゼロをすべて削除します。

# 例

```jldoctest
julia> x = dec"1.2000"
1.2000

julia> x.c # `x` の係数
12000

julia> y = normalize(dec"1.2000")
1.2

julia> y.c # `y` の係数
12

julia> x == y
true
```
