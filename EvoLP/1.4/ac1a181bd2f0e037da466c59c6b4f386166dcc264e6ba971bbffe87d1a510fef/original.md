```
circle(x)
```

!!! warning "Deprecated from EvoLP 1.3"
    This test function will be **deprecated** in a future major release.


The **circle** function is a multiobjective test function, given by

$$
f(x) = \begin{bmatrix}
        1 - r\cos(\theta) \\
        1 - r\sin(\theta)
        \end{bmatrix}
$$

where $\theta=x_1$ and $r$ is obtained by

$$
r = \frac{1}{2} + \frac{1}{2} \left(\frac{2x_2}{1+x_2^2}\right)
$$
