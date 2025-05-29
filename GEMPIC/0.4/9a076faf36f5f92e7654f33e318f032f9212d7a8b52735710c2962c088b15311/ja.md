```
compute_b_from_e!(b, solver, delta_t, e)
```

EyからBzを計算するために、スプライン係数に対して強い1Dファラデー方程式を使用します。$B_z^{new}(x_j) = B_z^{old}(x_j) - \frac{\Delta t}{\Delta x} (E_y(x_j) - E_y(x_{j-1})$

離散カール行列を掛けることによって。
