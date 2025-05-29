```
fit_line(x::AbstractVector, y::AbstractVector)
```

データ `x, y` に線形方程式をフィットさせます。`m, b` を返します。

$$
y = mx + b
$$

`Optim` に依存します。
