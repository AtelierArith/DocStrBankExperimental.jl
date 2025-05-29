```
divergence(f, x)
```

ベクトル場 `f` の発散を点 `x` で計算します。

# 例

```jldoctest
julia> f(x) = 2x;

julia> x = rand(Vec{3});

julia> divergence(f, x)
6.0
```
