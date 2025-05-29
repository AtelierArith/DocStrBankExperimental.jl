```
SKCE(k; unbiased::Bool=true, blocksize=identity)
```

Estimator of the squared kernel calibration error (SKCE) with kernel `k`.

Kernel `k` on the product space of predictions and targets has to be a `Kernel` from the Julia package [KernelFunctions.jl](https://github.com/JuliaGaussianProcesses/KernelFunctions.jl) that can be evaluated for inputs that are tuples of predictions and targets.

One can choose an unbiased or a biased variant with `unbiased=true` or `unbiased=false`, respectively (see details below).

The SKCE is estimated as the average estimate of different blocks of samples. The number of samples per block is set by `blocksize`:

  * If `blocksize` is a function `blocksize(n::Int)`, then the number of samples per block is set to `blocksize(n)` where `n` is the total number of samples.
  * If `blocksize` is an integer, then the number of samplers per block is set to `blocksize`, indepedent of the total number of samples.

The default setting `blocksize=identity` implies that a single block with all samples is used.

The number of samples per block must be at least 1 if `unbiased=false` and 2 if `unbiased=true`. Additionally, it must be at most the total number of samples. Note that the last block is neglected if it is incomplete (see details below).

# Details

The unbiased estimator is not guaranteed to be non-negative whereas the biased estimator is always non-negative.

The sample complexity of the estimator is $O(mn)$, where $m$ is the block size and $n$ is the total number of samples. In particular, with the default setting `blocksize=identity` the estimator has a quadratic sample complexity.

Let $(P_{X_i}, Y_i)_{i=1,\ldots,n}$ be a data set of predictions and corresponding targets. The estimator with block size $m$ is defined as

$$
{\bigg\lfloor \frac{n}{m} \bigg\rfloor}^{-1} \sum_{b=1}^{\lfloor n/m \rfloor}
|B_b|^{-1} \sum_{(i, j) \in B_b} h_k\big((P_{X_i}, Y_i), (P_{X_j}, Y_j)\big),
$$

where

$$
\begin{aligned}
h_k\big((μ, y), (μ', y')\big) ={}&   k\big((μ, y), (μ', y')\big)
                                   - 𝔼_{Z ∼ μ} k\big((μ, Z), (μ', y')\big) \\
                                 & - 𝔼_{Z' ∼ μ'} k\big((μ, y), (μ', Z')\big)
                                   + 𝔼_{Z ∼ μ, Z' ∼ μ'} k\big((μ, Z), (μ', Z')\big)
\end{aligned}
$$

and blocks $B_b$ ($b = 1, \ldots, \lfloor n/m \rfloor$) are defined as

$$
B_b = \begin{cases}
\{(i, j): (b - 1) m < i < j \leq bm \} & \text{(unbiased)}, \\
\{(i, j): (b - 1) m < i, j \leq bm \} & \text{(biased)}.
\end{cases}
$$

# References

Widmann, D., Lindsten, F., & Zachariah, D. (2019). [Calibration tests in multi-class classification: A unifying framework](https://proceedings.neurips.cc/paper/2019/hash/1c336b8080f82bcc2cd2499b4c57261d-Abstract.html). In: Advances in Neural Information Processing Systems (NeurIPS 2019) (pp. 12257–12267).

Widmann, D., Lindsten, F., & Zachariah, D. (2021). [Calibration tests beyond classification](https://openreview.net/forum?id=-bxf89v3Nx).
