```
x, w = logweight(T, n, r=0, endpt=neither)
```

は、重み関数

```
w(x) = xʳ log(1/x),    r ≥ 0.
```

を持つ区間 `0 < x < 1` における n 点ガウスルールの点 `x` と重み `w` を返します。
