```
r_from_rstar(a, rstar)
```

Convert a tortoise coordinate `rstar` to the corresponding Boyer-Lindquist coordiante `r`.  It uses a bisection method when `rstar <= 0`, and Newton method otherwise.

The function assumes that $r \geq r_{+}$ where $r_{+}$ is the outer event horizon.
