```
sweep!(A, k ; inv=false)
sweep!(A, ks; inv=false)
```

行列 `A` の要素 `k`（または `ks` の各要素）に対してスイープ操作（または `inv=true` の場合は逆スイープ）を実行します。上三角のみが読み取られ/スイープされます。

# 例:

```
x = randn(100, 10)
xtx = x'x
sweep!(xtx, 1)
sweep!(xtx, 1, true)
```
