```
maximal_order(K::NumField{QQFieldElem}; discriminant::ZZRingElem, ramified_primes::Vector{ZZRingElem}) -> AbsNumFieldOrder
```

$$
K
$$

の最大のオーダーを返します。既に知られている場合は、最大のオーダーの分解体や、分岐素数などの追加情報を提供できます。

# 例

```julia-repl
julia> Qx, x = QQ["x"];
julia> K, a = number_field(x^3 + 2, "a");
julia> O = maximal_order(K);
```
