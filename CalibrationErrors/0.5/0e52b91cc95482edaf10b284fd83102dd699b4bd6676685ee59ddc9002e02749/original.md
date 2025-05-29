```
UCME(k, testpredictions, testtargets)
```

Estimator of the unnormalized calibration mean embedding (UCME) with kernel `k` and sets of `testpredictions` and `testtargets`.

Kernel `k` on the product space of predictions and targets has to be a `Kernel` from the Julia package [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) that can be evaluated for inputs that are tuples of predictions and targets.

The number of test predictions and test targets must be the same and at least one.

# Details

The estimator is biased and guaranteed to be non-negative. Its sample complexity is $O(mn)$, where $m$ is the number of test locations and $n$ is the total number of samples.

Let $(T_i)_{i=1,\ldots,m}$ be the set of test locations, i.e., test predictions and corresponding targets, and let $(P_{X_j}, Y_j)_{j=1,\ldots,n}$ be a data set of predictions and corresponding targets. The plug-in estimator of $\mathrm{UCME}_{k,m}^2$ is defined as

$$
m^{-1} \sum_{i=1}^{m} {\bigg(n^{-1} \sum_{j=1}^n k\big(T_i, (P_{X_j}, Y_j)\big)
- \mathbb{E}_{Z \sim P_{X_j}} k\big(T_i, (P_{X_j}, Z)\big)\bigg)}^2.
$$

# References

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx). To be presented at *ICLR 2021*.
