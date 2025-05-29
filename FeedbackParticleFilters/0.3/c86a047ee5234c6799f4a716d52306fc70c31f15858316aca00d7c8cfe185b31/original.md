```
DifferentialRKHSMethodS1(epsilon, lambda)
```

Differential loss reproducing kernel Hilbert space (RKHS) method on the circle, adapted from [1], Section III. The kernel is a von Mises kernel.

### Parameters

  * `kappa`:  scale parameter of the von Mises kernel. Large values produce a narrow kernel.
  * `lambda`: regularization parameter, Eq. 20 in [1]

### Reference

[1] Radhakrishnan, A. & and Meyn, S. (2018). Feedback particle filter design using a differential-loss reproducing kernel Hilbert space. 2018 Annual American Control Conference (ACC). IEEE. https://doi.org/10.23919/ACC.2018.8431689
