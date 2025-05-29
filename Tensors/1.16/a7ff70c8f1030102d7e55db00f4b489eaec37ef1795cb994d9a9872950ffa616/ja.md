```
curl(f, x)
```

ベクトル場 `f` のカールを点 `x` で計算します。

# 例

```jldoctest
julia> f(x) = Vec{3}((x[2], x[3], -x[1]));

julia> x = rand(Vec{3});

julia> curl(f, x)
3-element Vec{3, Float64}:
 -1.0
  1.0
 -1.0
```
