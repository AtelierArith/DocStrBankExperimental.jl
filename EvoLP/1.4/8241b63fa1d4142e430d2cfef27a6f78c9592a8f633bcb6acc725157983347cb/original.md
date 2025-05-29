```
flower(x; a=1, b=1, c=4)
```

!!! warning "Deprecated from EvoLP 1.3"
    This function will be **deprecated** in a future major release.


The **flower** function is a two-dimensional test function with flower-like contour lines coming out from the origin. Typically, optional parameters are set at $a=1$, $b=1$ and $c=4$. The function is minimised near the origin, although it does not have a global minimum due to `atan` bein undefined at $[0, 0]$.

$$
f(x) = a\lVert\mathbb{x}\rVert + b \sin(c\arctan(x_2, x_1))
$$
