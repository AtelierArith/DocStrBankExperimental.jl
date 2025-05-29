```
homogenize(sys::SOACS)
```

Transform an inhomogeneous second order system into a homogeneous one by introducing auxiliary state variables.

### Input

  * `sys` – second order system

### Output

First-order homogeneous system.

### Notes

This function transforms the second-order system $Mx'' + Cx' + Kx = b$ into a first-order, homogeneous one, $y' = Â * y$. It is assumed that the matrix $M$ is invertible.
