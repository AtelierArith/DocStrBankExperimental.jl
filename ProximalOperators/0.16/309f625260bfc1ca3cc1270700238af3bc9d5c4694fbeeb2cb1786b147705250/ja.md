```
IndPolyhedral([l,] A, [u, xmin, xmax])
```

多面体集合の指示関数を返します：

$$
S = \{ x : x_\min \leq x \leq x_\max, l \leq Ax \leq u \}.
$$

行列 `A` は必須の引数です。境界のいずれかが提供されていない場合、それは（プラスまたはマイナスの）無限大であると見なされます。
