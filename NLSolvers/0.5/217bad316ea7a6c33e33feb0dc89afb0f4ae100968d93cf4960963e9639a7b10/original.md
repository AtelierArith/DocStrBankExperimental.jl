```
HZAW
```

An object that controls the Hager-Zhang approximate Wolfe line search algorithm.[^HZ2005]

```
HZAW(; kwargs...)
```

The `HZAW` constructor takes the following keyword arguments. Default values correspond to those used in section 5 of [^HZ2005].

  * `decrease`: parameter between 0 and 1, less than or equal to `curvature`, specifying sufficient decrease in the objective per the Armijo rule. Defaults to 0.1.
  * `curvature`: parameter between 0 and 1, greater than or equal to `decrease`, specifying sufficient decrease in the gradient per the curvature condition. Defaults to 0.9.
  * `theta`: parameter between 0 and 1 that controls the bracketing interval update. Defaults to 1/2, which indicates bisection. (See step U3 of the interval update procedure in section 4 of [^HZ2005].)
  * `gamma`: factor by which the length of the bracketing interval decreases at each iteration of the algorithm. Defaults to 2/3.

We tweak the original algorithm slightly, by backtracking into a feasible region if the original step length results in function values that are not finite.

[^HZ2005]: Hager, W. W., & Zhang, H. (2005). A New Conjugate Gradient Method        with Guaranteed Descent and an Efficient Line Search. SIAM Journal        on Optimization, 16(1), 170–192. doi:10.1137/030601880
