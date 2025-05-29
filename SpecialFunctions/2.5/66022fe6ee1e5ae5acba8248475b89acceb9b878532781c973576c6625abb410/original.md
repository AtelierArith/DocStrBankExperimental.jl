```
expinti(x::Real)
```

Computes the exponential integral function

$$
\operatorname{Ei}(x) = \int_{-\infty}^x \frac{e^t}{t} \mathrm{d}t,
$$

which is equivalent to $-\Re[\operatorname{E}_1(-x)]$ where $\operatorname{E}_1$ is the `expint` function.
