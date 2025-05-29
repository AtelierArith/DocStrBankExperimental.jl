```
controllability(A, B; atol, rtol)
controllability(sys; atol, rtol)
```

ペア `(A, B)` または `sys` の制御可能性を PHB テストを使用して確認します。

返される値には、`iscontrollable` フィールドが含まれており、これは `A` のすべての固有値でランク条件が満たされている場合は `true`、そうでない場合は `false` です。返される構造体には、`A` の各固有値におけるランクと最小特異値が `ranks` および `sigma_min` フィールドに含まれています。

技術的には、この関数は原点からの制御可能性、つまり到達可能性をチェックします。
