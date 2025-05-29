```
correlationsum(X, ε::Real; w = 0, norm = Euclidean(), q = 2) → C_q(ε)
```

Calculate the `q`-order correlation sum of `X` (`StateSpaceSet` or timeseries) for a given radius `ε` and `norm`. They keyword `show_progress = true` can be used to display a progress bar for large `X`.

```
correlationsum(X, εs::AbstractVector; w, norm, q) → C_q(ε)
```

If `εs` is a vector, `C_q` is calculated for each `ε ∈ εs` more efficiently. Multithreading is also enabled over the available threads (`Threads.nthreads()`). The function [`boxed_correlationsum`](@ref) is typically faster if the dimension of `X` is small and if `maximum(εs)` is smaller than the size of `X`.

## Keyword arguments

  * `q = 2`: order of the correlation sum
  * `norm = Euclidean()`: distance norm
  * `w = 0`: Theiler window
  * `show_progress = true`: display a progress bar

## Description

The correlation sum is defined as follows for `q=2`:

$$
C_2(\epsilon) = \frac{2}{(N-w)(N-w-1)}\sum_{i=1}^{N}\sum_{j=1+w+i}^{N}
B(||X_i - X_j|| < \epsilon)
$$

for as follows for `q≠2`

$$
C_q(\epsilon) = \left[ \sum_{i=1}^{N} \alpha_i
\left[\sum_{j:|i-j| > w} B(||X_i - X_j|| < \epsilon)\right]^{q-1}\right]^{1/(q-1)}
$$

where

$$
\alpha_i = 1 / (N (\max(N-w, i) - \min(w + 1, i))^{(q-1)})
$$

with $N$ the length of `X` and $B$ gives 1 if its argument is `true`. `w` is the [Theiler window](@ref).

See the article of Grassberger for the general definition [Grassberger2007](@cite) and the book "Nonlinear Time Series Analysis" [Kantz2003](@cite), Ch. 6, for a discussion around choosing best values for `w`, and Ch. 11.3 for the explicit definition of the q-order correlationsum. Note that the formula in 11.3 is incorrect, but corrected here, indices are adapted to take advantage of all available points and also note that we immediatelly exponentiate $C_q$ to $1/(q-1)$, so that it scales exponentially as $C_q \propto \varepsilon ^\Delta_q$ versus the size $\varepsilon$.
