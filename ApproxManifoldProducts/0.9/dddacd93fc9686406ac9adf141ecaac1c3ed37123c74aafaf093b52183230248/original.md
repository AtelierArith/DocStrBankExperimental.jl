```julia
manifoldLooCrossValidation(pts, bw; own, diffop)

```

Calculate negative entropy with leave one out (j'th element) cross validation.

# Background

From: Silverman, B.: Density Estimation for Statistics and Data Analysis, 1986, p.52

Probability density function `p(x)`, as estimated by kernels

$$
hatp_{-j}(x) = 1/(N-1) Σ_{i != j}^N frac{1}{sqrt{2pi}σ } exp{ -frac{(x-μ)^2}{2 σ^2} }
$$

and has Cross Validation number as the average log evaluations of leave one out `hatp_{-j}(x)`:

$$
CV(p) = 1/N Σ_i^N log hat{p}_{-j}(x_i)
$$

This quantity `CV` is related to an entropy `H(p)` estimate via:

$$
H(p) = -CV(p)
$$
