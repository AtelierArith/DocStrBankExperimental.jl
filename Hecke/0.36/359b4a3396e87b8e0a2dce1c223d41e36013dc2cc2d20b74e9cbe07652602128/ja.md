```
a_invariants(E::EllipticCurve{T}) -> Tuple{T, T, T, T, T}
```

$$
E
$$

のワイエルシュトラス係数をタプル$(a_1, a_2, a_3, a_4, a_6)$として返します。ここで、$E$は$y^2 + a_1xy + a_3y = x^3 + a_2x^2 + a_4x + a_6$で与えられます。
