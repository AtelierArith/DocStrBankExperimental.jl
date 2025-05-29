```
tangent(f::Function, c)
```

`f`のグラフにおける点`x=c`での接線を表す関数を返します。

例。接線はy軸とどこで交差しますか？

```
f(x) = sin(x)
tl = tangent(f, pi/4)  # または tl(x) = tangent(f, pi/3)(x) で一般的な関数を使用
tl(0)
```

`f`の自動微分を使用して、`x=c`での接線の傾きを求めます。
