```
HOErrorControl()
```

Higher order global error estimation method

Uses a solution from order+2 method on the original mesh and calculate the error with

$$
error = \max\frac{u_p - u_{p+2}}{1 + |u_p|}
$$
