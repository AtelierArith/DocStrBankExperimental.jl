```
isolines(xs, ys, zs; lift = false, interpolation = :cubic)
```

関数の等高線をプロットします。関数の値は配列（または関数）`zs`によって表されます。`lift`がtrueの場合、3Dでプロットします。

# 例

```julia-repl julia> isolines(0:10, 0:10, (x,y) -> (100 - x^2 + y^2)/10, lift = true)

```
