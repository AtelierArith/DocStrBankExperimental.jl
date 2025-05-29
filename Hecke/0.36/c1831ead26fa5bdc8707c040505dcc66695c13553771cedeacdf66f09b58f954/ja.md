```
coefficients(E::EllipticCurve{T}) -> Tuple{T, T, T, T, T}
```

$$
E
$$

のワイエルシュトラス係数をタプル(a1, a2, a3, a4, a6)として返します。ここで、$E$はy^2 + a1xy + a3y = x^3 + a2x^2 + a4x + a6によって与えられます。
