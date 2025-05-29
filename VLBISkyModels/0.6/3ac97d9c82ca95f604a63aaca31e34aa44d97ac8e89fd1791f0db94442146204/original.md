```
$(TYPEDEF)
```

Uses the basis spline (BSpline) kernel of order `N`. These are the kernel that come from recursively convolving the tophat kernel

$$
    B_0(x) = \begin{cases} 1 & |x| < 1 \\ 0 & otherwise \end{cases}
$$

`N` times.

## Notes

BSpline kernels have a number of nice properties:

1. Simple frequency response $\sinc(u/2)^N$
2. preserve total intensity

For `N`>1 these kernels aren't actually interpolation kernels however, this doesn't matter for us.

Currently only the 0,1,3 order kernels are implemented.
