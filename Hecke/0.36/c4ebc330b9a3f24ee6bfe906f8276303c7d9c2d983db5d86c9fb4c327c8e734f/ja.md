```
complex_conjugation(C::ClassField, p::InfPlc)
```

無限位 `p` が `C` で分岐する場合、`p` を拡張する複素埋め込みに対して複素共役を誘導する `number_field(C)` の自己同型を返します。

```jldoctest
julia> K, = quadratic_field(21);

julia> OK = maximal_order(K);

julia> C = ray_class_field(6 * OK, real_places(K));

julia> complex_conjugation(C, real_places(K)[1]);
```
