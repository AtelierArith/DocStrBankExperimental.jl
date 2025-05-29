```
PolynomialLimbDark(u::AbstractVector)
```

Polynomial limb darkening using analytical integrals. The length of the `u` vector is equivalent to the order of polynomial used; e.g., `[0.2, 0.3]` corresponds to quadratic limb darkening.

# Mathematical form

$$
I(\mu) \propto 1 - u_1(1-\mu) - u_2(1-\mu)^2 - \dots - u_N(1-\mu)^N
$$

which is equivalent to the series

$$
I(\mu) \propto -\sum_{i=0}^N{u_i(1-\mu)^i}
$$

with the definition $u_0 \equiv -1$.

# Examples

```jldoctest poly
u = [0.4, 0.26] # quadratic and below is 100% analytical
ld = PolynomialLimbDark(u)
ld(0.1, 0.01)

# output
0.9998787880717668
```

```jldoctest poly
u2 = vcat(u, ones(12) ./ 12)
ld2 = PolynomialLimbDark(u2)
ld2(0.1, 0.01)

# output
0.9998740059086433
```

# References

> [Agol, Luger, Foreman-Mackey (2020)](https://ui.adsabs.harvard.edu/abs/2020AJ....159..123A)
>
> "Analytic Planetary Transit Light Curves and Derivatives for Stars with Polynomial Limb Darkening"


> [Luger et al. (2019)](https://ui.adsabs.harvard.edu/abs/2019AJ....157...64L)
>
> "starry: Analytic Occultation Light Curves"

