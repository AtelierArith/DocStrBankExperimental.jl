```
quadratic_estimate(ds::DataSet, which; wiener_filtered=true)
quadratic_estimate((ds₁::DataSet, ds₂::DataSet), which; wiener_filtered=true)
```

Compute the quadratic estimate of `ϕ` given data.

The `ds` or `(ds₁,ds₂)` tuple contain the DataSet object(s) which house the data and covariances used in the estimate. Note that only the Fourier-diagonal approximations for the beam, mask, and noise, i.e. `B̂`, `M̂`, and `Cn̂`, are accounted for. To account full operators (if they are not actually Fourier-diagonal), you should compute the impact using Monte Carlo.

If a tuple is passed in, the result will come from correlating the data from `ds₁` with that from `ds₂`.

An optional keyword argument `AL` can be passed in case the QE normalization was already computed, in which case it won't be recomputed during the calculation.

Returns a named tuple of `(;ϕqe, AL, Nϕ)` where `ϕqe` is the (possibly Wiener filtered, depending on `wiener_filtered` option) quadratic estimate, `AL` is the normalization (which is already applied to ϕqe, it does not need to be applied again), and `Nϕ` is the analytic N⁰ noise bias (Nϕ==AL if using unlensed weights, currently only Nϕ==AL is always returned, no matter the weights)
