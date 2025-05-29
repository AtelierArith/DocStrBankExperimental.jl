```
number_field(p::InfPlc) -> NumField
```

無限位の数体を返します。

# 例

```jldoctest
julia> K, = quadratic_field(5);

julia> p = infinite_places(K)[1];

julia> number_field(p) == K
true
```
