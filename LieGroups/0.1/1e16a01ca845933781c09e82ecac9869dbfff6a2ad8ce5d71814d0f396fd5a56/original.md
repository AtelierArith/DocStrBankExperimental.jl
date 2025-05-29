```
exp(::GeneralLinearGroup, X)
exp!(::GeneralLinearGroup, g, X)
```

Compute the Lie group exponential on the [`GeneralLinearGroup`](@ref), which is given by the [matrix exponential](https://en.wikipedia.org/wiki/Matrix_exponential)

$$
\exp X = \sum_{k=0}^{∞} \frac{1}{k!}X^k
$$

see also [HilgertNeeb:2012; Example 9.2.3 (b)](@cite)
