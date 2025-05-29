```
move_block!(mpc,block)
```

Reduce the number of controls by keeping it constant in blocks. For example, `block`=[2,1,3] keeps the control constant for 2 time-steps, 1 time step, and 3 time steps.

  * if sum(block) ≠ mpc.Np, the resulting block will be padded or clipped
  * if `block` is an Int, a vector with constant block size is created
