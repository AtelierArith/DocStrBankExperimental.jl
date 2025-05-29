```
subfield(L::NumField, elements::Vector{<: NumFieldelem};
                      is_basis::Bool = false) -> NumField, Map
```

与えられた要素によって生成される単純数体 $K$ を、基底体 $k$ の上で $L$ から返します。埋め込み $k \to L$ も返されます。

`is_basis` が `true` の場合、`elements` が $K$ の $k$-基底を保持していると仮定されます。

```jldoctest
julia> Qx, x = QQ[:x]; L, a = number_field(x^4 + 6*x^2 + 4, :a);

julia> K, KtoL = subfield(L, [a^2]);

julia> K
Number field with defining polynomial x^2 + 6*x + 4
  over rational field
```
