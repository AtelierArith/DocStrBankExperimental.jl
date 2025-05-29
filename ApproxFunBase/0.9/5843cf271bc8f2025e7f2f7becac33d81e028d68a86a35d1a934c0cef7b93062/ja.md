```
Fun(f, d::Domain)
```

指定されたドメインのデフォルト空間を使用する、すなわち `Fun(f, Space(d))` を返します。

# 例

```jldoctest
julia> f = Fun(x->x^2, 0..1);

julia> f(0.1) ≈ (0.1)^2
true
```
