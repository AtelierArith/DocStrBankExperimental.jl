```
laglink(a, M; [Ts])
```

位相遅れリンクを返します。目安として `a = 0.1ωc` を使用すると、6度未満の位相余裕損失が保証されます。ボード線図は `M` から始まり、`a/M` で下に曲がり、周波数が `a` を超えると1で水平になります。

$$
\dfrac{s + a}{s + a/M} = M \dfrac{1 + s/a}{1 + sM/a}
$$
