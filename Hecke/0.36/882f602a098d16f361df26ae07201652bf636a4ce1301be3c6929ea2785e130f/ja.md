```
is_negative(a::NumFieldElem, embs::Vector{NumFieldEmb}) -> Bool
```

要素 $a$ が `embs` のすべての埋め込みで正であるかどうかを返します。`embs` のすべての埋め込みは実数でなければなりません。

# 例

```jldoctest
julia> K, a  = quadratic_field(5);

julia> e = complex_embedding(K, -2.1);

julia> e(a)
[-2.236067977 +/- 5.02e-10]

julia> is_negative(a, [e])
true
```
