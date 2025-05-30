```
x, w = chebyshev(T, n, kind=1, endpt=neither)
```

は、重み関数を持つ区間 `-1 < x < 1` に対する `n` 点のガウス・チェビシェフルールの点 `x` と重み `w` を返します。

```
w(x) = 1 / sqrt(1-x²)   もし kind=1 の場合
w(x) = sqrt(1-x²)       もし kind=2 の場合。
```

左ラデュー、右ラデュー、またはロバットルールの場合は、それぞれ `endpt=left`、`right` または `both` を使用してください。
