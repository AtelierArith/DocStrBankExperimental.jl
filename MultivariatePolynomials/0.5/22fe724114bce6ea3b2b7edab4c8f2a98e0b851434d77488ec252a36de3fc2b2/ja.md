```
divides(t1::AbstractTermLike, t2::AbstractTermLike)
```

t1の単項式がt2の単項式を割り切るかどうかを返します。

### 例

`divides(2x^2y, 3xy)`を呼び出すと、`x^2y`は`xy`を割り切らないため、falseを返すべきです。なぜなら、`x^2y`の`x`の次数は2であり、`xy`の`x`の次数よりも大きいためです。しかし、`divides(3xy, 2x^2y)`を呼び出すと、trueを返すべきです。
