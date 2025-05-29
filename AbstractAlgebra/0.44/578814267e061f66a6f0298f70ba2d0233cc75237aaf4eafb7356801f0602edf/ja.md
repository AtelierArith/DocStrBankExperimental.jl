```
leading_exponent_vector(p::MPolyRingElem)
```

$$
p
$$

の先頭項の指数ベクトルを返します。返されるのは、先頭項の各変数の指数を示すJuliaの1次元配列です。この関数は、$p$がゼロの場合に`ArgumentError`をスローします。
