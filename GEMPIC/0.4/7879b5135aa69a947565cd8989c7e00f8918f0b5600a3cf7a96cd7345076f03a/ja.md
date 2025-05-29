```
compute_b_from_e!( field_out, maxwell_solver, delta_t, field_in)
```

Eyを使用して強い1Dファラデー方程式に基づいてBzを計算します

$$
B_z^{new}(x_j) = B_z^{old}(x_j) - \frac{\Delta t}{\Delta x} (E_y(x_j) - E_y(x_{j-1})
$$
