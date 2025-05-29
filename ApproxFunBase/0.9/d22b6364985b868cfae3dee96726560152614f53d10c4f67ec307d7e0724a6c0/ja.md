```
(s::Space)(n::Integer, points...)
```

ベクトルの係数を割り当てることなく、`Fun(s, [zeros(n); 1])(points...)` を効率的に評価します。

# 例

```jldoctest
julia> Chebyshev()(1, 0.5)
0.5
```
