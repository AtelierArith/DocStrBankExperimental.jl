```
make_supercell(g::PeriodicGraph, t)
```

入力 `g` に同型のグラフを返します。その単位セルは `g` の単位セルの繰り返しであり、各次元 `i` は `t[i]` 回繰り返されます。したがって、`make_supercell(g, t)` の頂点の数は `prod(t)*nv(g)` です。

`t` は正の整数のイテレータでなければなりません。
