```
issymmorph(sgnum::Integer, D::Integer=3) --> Bool
```

与えられた空間群番号 `sgnum` と次元 `D` に対して、その空間群が対称的であるか（`true`）非対称的であるか（`false`）を返します。

`issymmorph(spacegroup(sgnum, D))` と同等ですが、パフォーマンスのためにメモ化を使用します。
