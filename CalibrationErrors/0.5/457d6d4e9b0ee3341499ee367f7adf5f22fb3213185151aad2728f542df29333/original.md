```
UnbiasedSKCE(k)
```

Unbiased estimator of the squared kernel calibration error (SKCE) with kernel `k`.

Kernel `k` on the product space of predictions and targets has to be a `Kernel` from the Julia package [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) that can be evaluated for inputs that are tuples of predictions and targets.

# Details

The estimator is unbiased and not guaranteed to be non-negative. Its sample complexity is $O(n^2)$, where $n$ is the total number of samples.

Let $(P_{X_i}, Y_i)_{i=1,\ldots,n}$ be a data set of predictions and corresponding targets. The estimator is defined as

$$
\frac{2}{n(n-1)} \sum_{1 \leq i < j \leq n} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

where

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big).
\end{aligned}
$$

# References

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [Calibration tests in multi-class classification: A unifying framework](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx).

See also: [`BiasedSKCE`](@ref), [`BlockUnbiasedSKCE`](@ref)
