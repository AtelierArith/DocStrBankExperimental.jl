```
create_lagrange_differentiation_matrix(k::Int)
```

Lagrange differentiation matrix, $m[i,j]=s_{k-j}^k(i)$, for $k^{th}$-order lagrangian differentiation,

$$
\frac{dy}{dx}[i]= \sum_{j=0}^{k}m[i,j]y[j],
$$

#### Example:

```
k = 3
create_lagrange_differentiation_matrix(k)
 4×4 Matrix{Rational{Int64}}:
  -11//6   3//1  -3//2   1//3
   -1//3  -1//2   1//1  -1//6
    1//6  -1//1   1//2   1//3
   -1//3   3//2  -3//1  11//6
```
