```
gaunt_coefficient(l1,m1,l2,m2,l3,m3)
```

二つの球面調和関数の積を書くために使用されるガウント係数のバージョンです。もし Y_{l,m} が量子力学からの典型的な位相規約を持つ複素球面調和関数であるならば：

```
gaunt_coefficient(l1,m1,l2,m2,l3,m3) = 4*π*im^{l2+l3-l1} Integral[Y_{l1,m1}*conj(Y_{l2,m2})*conj(Y_{l3,m3})]
```

ここで、積分は固体角にわたります。

最も標準的なガウント係数 `G(l1,m1;l2,m2;l3)` は、次の恒等式を通じて関連しています：

```
4pi * G(l1,m1;l2,m2;l3) = im^(l1-l2-l3) * (-1)^m2 * gaunt_coefficient(l1,m1,l2,-m2,l3,m1+m2)
```
