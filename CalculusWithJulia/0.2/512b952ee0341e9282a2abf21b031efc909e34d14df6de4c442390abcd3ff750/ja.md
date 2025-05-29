```
secant(f::Function, a, b)
```

`f`のグラフにおける`x=a`および`x=b`での接線を表す関数を返します。

例。接線は`y`軸とどこで交差しますか？

```
f(x) = sin(x)
a, b = pi/4, pi/3
sl = secant(f, a, b)  # または sl(x) = secant(f, a, b)(x) を使って一般的な関数を使用
sl(0)
```
