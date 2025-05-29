```julia
logistic(x)

```

The [logistic](https://en.wikipedia.org/wiki/Logistic_function) sigmoid function mapping a real number to a value in the interval $[0,1]$,

$$
\sigma(x) = \frac{1}{e^{-x} + 1} = \frac{e^x}{1+e^x}.
$$

Its inverse is the [`logit`](@ref) function.
