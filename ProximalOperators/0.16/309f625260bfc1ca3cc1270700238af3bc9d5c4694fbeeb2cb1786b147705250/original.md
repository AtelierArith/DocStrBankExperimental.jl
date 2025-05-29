```
IndPolyhedral([l,] A, [u, xmin, xmax])
```

Return the indicator function of the polyhedral set:

$$
S = \{ x : x_\min \leq x \leq x_\max, l \leq Ax \leq u \}.
$$

Matrix `A` is a mandatory argument; when any of the bounds is not provided, it is assumed to be (plus or minus) infinity.
