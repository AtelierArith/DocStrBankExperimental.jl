```
is_real(p::InfPlc) -> Bool
```

無限位 `p` が実数であるかどうかを返します。

```jldoctest
julia> K, = quadratic_field(3);

julia> is_real(infinite_places(K)[1])
true
```
