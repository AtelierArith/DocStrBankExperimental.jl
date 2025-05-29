```
isfeasible(bounds::ConstraintBounds, x) -> Bool
```

`x`が`lx`、`ux`、`lc`、および`uc`を持つ`bounds`オブジェクトに対して実行可能である場合、`true`を返します。`x`が実行可能であるためには、次の条件を満たす必要があります。

```
lx[i] <= x[i] <= ux[i]
lc[i] <= c(x)[i] <= uc[i]
```

すべての可能な`i`について。
