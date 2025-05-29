```
convective_derivative_rot!(out,q)
```

Compute the rotational form of the convective derivative of `q` in the form $\frac{1}{2}\nabla|u|^2-u\times(\nabla\times u)$ and put the result into `out`. Note that the result is not scaled by any grid spacing.
