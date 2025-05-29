```
kpm_dot(
    coefs::T, moments::T
) where {T<:AbstractVector}
```

Calculate the inner product

$$
\langle c | \mu \rangle = \sum_{m=1}^M c_m \cdot \mu_m,
$$

where $c_m$ are the KPM expansion coefficients, and $\mu_m$ are the KPM moments.
