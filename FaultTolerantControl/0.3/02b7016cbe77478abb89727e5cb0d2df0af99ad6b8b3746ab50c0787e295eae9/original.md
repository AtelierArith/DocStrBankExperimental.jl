```
empirical_gramian()
```

A function for computation of controllability or observability gramian.

# References

[1] M. Tahavori and A. Hasan, “Fault recoverability for nonlinear systems with application to fault tolerant control of UAVs,” Aerosp. Sci. Technol., vol. 107, p. 106282, 2020, doi: 10.1016/j.ast.2020.106282. [2] C. Himpe, “emgr-The empirical Gramian framework,” Algorithms, vol. 11, no. 7, pp. 1–27, 2018, doi: 10.3390/a11070091.

# Notes

  * f = function of (x, u, p, t)
  * g = function of (x, u, p, t)
  * pr = parameter vector(s), each column i sone parameter sample
  * xs = steady-state and nominal initial state x_0
  * us = steady-state input
  * opt = :c for controllability gramian and :o for observability gramian
