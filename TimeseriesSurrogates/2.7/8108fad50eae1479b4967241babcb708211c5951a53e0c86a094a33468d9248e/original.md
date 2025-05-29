```
IAAFT(M = 100, tol = 1e-6, W = 75)
```

An iteratively adjusted amplitude-adjusted-fourier-transform surrogate[^SchreiberSchmitz1996].

IAAFT surrogates have the same linear correlation, or periodogram, and also preserves the amplitude distribution of the original data, but are improved relative to AAFT through iterative adjustment (which runs for a maximum of `M` steps). During the iterative adjustment, the periodograms of the original signal and the surrogate are coarse-grained and the powers are averaged over `W` equal-width frequency bins. The iteration procedure ends when the relative deviation between the periodograms is less than `tol` (or when `M` is reached).

IAAFT, just as AAFT, can be used to test the null hypothesis that the data come from a monotonic nonlinear transformation of a linear Gaussian process.

[^SchreiberSchmitz1996]: T. Schreiber; A. Schmitz (1996). "Improved Surrogate Data for Nonlinearity Tests". [Phys. Rev. Lett. 77 (4)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.77.635)
