```
derivative(f, x, ::Val{P})
derivative(f, x, l, ::Val{P})
derivative(f!, y, x, l, ::Val{P})
```

`f`の`P`-次方向微分をベクトル`x`に対して方向`l`で計算します。`x`が数値の場合、方向`l`は省略できます。
