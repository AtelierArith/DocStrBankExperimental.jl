```
expinti(x::Real)
```

指数関数積分関数を計算します

$$
\operatorname{Ei}(x) = \int_{-\infty}^x \frac{e^t}{t} \mathrm{d}t,
$$

これは $-\Re[\operatorname{E}_1(-x)]$ に相当し、ここで $\operatorname{E}_1$ は `expint` 関数です。
