```
compute_b_from_e!(b, solver, delta_t, e)
```

Compute Bz from Ey using strong 1D Faraday equation for spline coefficients $B_z^{new}(x_j) = B_z^{old}(x_j) - \frac{\Delta t}{\Delta x} (E_y(x_j) - E_y(x_{j-1})$

multiplying by discrete curl matrix
