```
principal_subfields(L::SimpleNumField) -> Vector{Tuple{NumField, Map}}
```

$$
L
$$

の主な部分体を、部分体$k$と埋め込み$k \to L$からなるペアとして返します。

# 例

```jldoctest
julia> Qx, x = QQ["x"];

julia> K, a = number_field(x^8 - x^4 + 1);

julia> length(principal_subfields(K))
8
```
