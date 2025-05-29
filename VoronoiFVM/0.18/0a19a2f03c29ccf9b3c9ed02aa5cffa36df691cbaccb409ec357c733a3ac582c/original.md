```julia
fbernoulli_pm(x)

```

Bernoulli function $B(x)=\frac{x}{e^x-1}$ for exponentially fitted upwind, joint evaluation for positive and negative argument

Usually, we need $B(x), B(-x)$ togehter,  and it is cheaper to calculate them together.

Returns two real numbers containing the result for argument `x` and argument `-x`.

The error in comparison with the evaluation of the original expression with BigFloat is less than 1.0e-15
