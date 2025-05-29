```
exp(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, X)
exp!(::LieGroup{ℝ, AbelianMultiplicationGroupOperation, Sphere}, g, X)
```

Compute the Lie group exponential on the [`CircleGroup`](@ref), represented as two dimensional vectors in the real plane. It coincides with the [ordinary complex exponential](https://en.wikipedia.org/wiki/Exponential_map_(Lie_theory)#Examples) after canonical identification of the real plane with the complex plane.

This can be computed in-place of `g`.

$$
\exp \begin{pmatrix} 0\\ t\end{pmatrix} = \begin{pmatrix} \cos(t)\\ \sin(t)\end{pmatrix}
$$
