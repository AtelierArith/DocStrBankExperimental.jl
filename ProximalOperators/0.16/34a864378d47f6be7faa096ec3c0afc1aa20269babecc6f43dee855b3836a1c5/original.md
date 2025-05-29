```
NormL21(λ=1, dim=1)
```

Return the "sum of $L_2$ norm" function

$$
f(X) = λ⋅∑_i\|x_i\|
$$

for a nonnegative `λ`, where $x_i$ is the $i$-th column of $X$ if `dim == 1`, and the $i$-th row of $X$ if `dim == 2`. In words, it is the sum of the Euclidean norms of the columns or rows.
