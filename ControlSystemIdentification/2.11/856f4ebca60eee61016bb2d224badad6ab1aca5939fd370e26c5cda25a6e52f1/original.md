```
H, N = tfest(data, σ = 0.05, method = :corr)
```

Estimate a transfer function model using the Correlogram approach (default) using the signal model $y = H(iω)u + n$.

Both `H` and `N` are of type `FRD` (frequency-response data).

  * `σ` determines the width of the Gaussian window applied to the estimated correlation functions before FFT. A larger `σ` implies less smoothing.
  * `H` = Syu/Suu             Process transfer function
  * `N` = Sy - |Syu|²/Suu     Estimated Noise PSD (also an estimate of the variance of $H$). Note that a PSD is related to the "noise model" $N_m$ used in the system identification literature as $N_{psd} = N_m^* N_m$. The magnitude curve of the noise model can be visualized by plotting `√(N)`.
  * `method`: `:welch` or `:corr`. `:welch` uses the Welch method to estimate the power spectral density, while `:corr` (default) uses the Correlogram approach. If `method = :welch`, the additional keyword arguments `n`, `noverlap` and `window` determine the number of samples per segment (default 10% of data), the number of samples to overlap between segments (default 50%), and the window function to use (default `hamming`), respectively.

# Extended help

This estimation method is unbiased if the input $u$ is uncorrelated with the noise $n$, but is otherwise biased (e.g., for identification in closed loop).
