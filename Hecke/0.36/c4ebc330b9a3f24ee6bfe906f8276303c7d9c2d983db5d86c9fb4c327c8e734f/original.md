```
complex_conjugation(C::ClassField, p::InfPlc)
```

Given an infinite place `p` ramifying in `C`, return the automorphism of `number_field(C)`, which induces complex conjugation on the complex embeddings extending `p`.

```jldoctest
julia> K, = quadratic_field(21);

julia> OK = maximal_order(K);

julia> C = ray_class_field(6 * OK, real_places(K));

julia> complex_conjugation(C, real_places(K)[1]);
```
