```
REErrorControl()
```

Richardson extrapolation global error estimation method

Use Richardson extrapolation to calculate the error on the doubled mesh with

$$
error = \frac{2^p}{2^p-1} * \max\frac{u_h - u_{h/2}}{1 + |u_h|}
$$
