```
exp(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, X)
exp!(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, X)
```

[`CircleGroup`](@ref)上のリー群指数を計算します。これは、実平面を複素平面と同一視した後、[通常の複素指数関数](https://en.wikipedia.org/wiki/Exponential_map_(Lie_theory)#Examples)と一致します。

これは`g`のインプレースで計算できます。

$$
\exp \begin{pmatrix} 0\\ t\end{pmatrix} = \begin{pmatrix} \cos(t)\\ \sin(t)\end{pmatrix}
$$
