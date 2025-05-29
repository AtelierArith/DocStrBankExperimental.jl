```
rangeclamp(f, hi=20, lo=-hi; replacement=NaN)
```

`f`を修正して、`f(x)`の値が`[lo,hi]`の範囲外の場合は`replacement`で置き換えます。

例

```
f(x) = 1/x
plot(rangeclamp(f), -1, 1)
plot(rangeclamp(f, 10), -1, 1) # `abs(y)`の値が10を超えない
```
