```
is_negative(a::NumFieldElem, e::NumFieldEmb)   -> Bool
```

数体要素 `a` と実埋め込み `e` が与えられたとき、`a` が `e` で正であるかどうかを返します。

# 例

```jldoctest
julia> K, a  = quadratic_field(5);

julia> e = complex_embedding(K, 2.1);

julia> is_negative(a, e)
false
```
