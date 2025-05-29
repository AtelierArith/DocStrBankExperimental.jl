```
exp(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, X)
exp!(::LieGroup{ℂ, AbelianMultiplicationGroupOperation, Circle{ℂ}}, g, X)
```

Computes the Lie group exponential on the complex [`CircleGroup`](@ref), which coincides with the [ordinary complex exponential](https://en.wikipedia.org/wiki/Exponential_map_(Lie_theory)#Examples).

The Lie algebra is precisely the imaginary axis of the complex plane.

This can be computed in-place of `g`.

$$
\exp (\mathrm{i}t) = \cos(t) + \mathrm{i}\sin(t)
$$
