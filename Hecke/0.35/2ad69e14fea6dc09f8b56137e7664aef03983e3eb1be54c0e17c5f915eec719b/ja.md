```
maximal_order(O::AbsNumFieldOrder; index_divisors::Vector{ZZRingElem}, discriminant::ZZRingElem, ramified_primes::Vector{ZZRingElem}) -> AbsNumFieldOrder
```

$$
O
$$

を含む数体の最大の位数を返します。既に知られている場合は、分岐素数、最大の位数の判別式、または最大の位数における$O$の指数を割る整数の集合を追加情報として提供できます。
