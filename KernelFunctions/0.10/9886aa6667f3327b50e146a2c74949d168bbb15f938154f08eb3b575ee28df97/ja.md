```
CosineKernel(; metric=Euclidean())
```

コサインカーネルは `metric` に関して定義されます。

# 定義

入力 $x, x'$ とメトリック $d(\cdot, \cdot)$ に対して、コサインカーネルは次のように定義されます。

$$
k(x, x') = \cos(\pi d(x, x')).
$$

デフォルトでは、$d$ はユークリッドメトリック $d(x, x') = \|x - x'\|_2$ です。
