```
integrate(a, r)
```

`a::HomogeneousPolynomial`を`r`-番目の変数に関して積分します。返される`HomogeneousPolynomial`には、追加の積分定数はありません。`a`の次数が`get_order()`に対応する場合、0次のゼロ`HomogeneousPolynomial`が返されます。
