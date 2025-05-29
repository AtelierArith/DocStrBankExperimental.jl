```
exp(::GeneralLinearGroup, X)
exp!(::GeneralLinearGroup, g, X)
```

[`GeneralLinearGroup`](@ref) におけるリー群の指数を計算します。これは [行列指数](https://en.wikipedia.org/wiki/Matrix_exponential) によって与えられます。

$$
\exp X = \sum_{k=0}^{∞} \frac{1}{k!}X^k
$$

また、[HilgertNeeb:2012; Example 9.2.3 (b)](@cite) も参照してください。
