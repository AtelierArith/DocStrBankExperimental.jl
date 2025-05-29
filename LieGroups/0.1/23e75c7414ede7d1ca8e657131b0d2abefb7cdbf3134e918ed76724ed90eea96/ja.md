```
exp(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, X)
exp!(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, X)
```

複素数の [`CircleGroup`](@ref) に対するリー群指数を計算します。これは [通常の複素指数関数](https://en.wikipedia.org/wiki/Exponential_map_(Lie_theory)#Examples) と一致します。

リー代数は正確に複素平面の虚軸です。

これは `g` のインプレースで計算できます。

$$
\exp (\mathrm{i}t) = \cos(t) + \mathrm{i}\sin(t)
$$
