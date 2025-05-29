```
SqrHingeLoss(y, μ=1)
```

Return the squared Hinge loss

$$
f(x) = μ⋅∑_i \max\{0, 1 - y_i ⋅ x_i\}^2,
$$

where `y` is an array and `μ` is a positive parameter.
