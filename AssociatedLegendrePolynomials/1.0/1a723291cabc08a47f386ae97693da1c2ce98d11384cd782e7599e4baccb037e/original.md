```
N = Nlm([T=Float64], l, m)
```

Computes the normalization constant

$$
    N_\ell^m \equiv \sqrt{\frac{2\ell+1}{4\pi} \frac{(\ell-m)!}{(\ell+m)!}}
$$

which defines the Spherical Harmonic normalized functions $\lambda_\ell^m(x)$ in terms of the standard unit normalized $P_\ell^m(x)$

$$
    \lambda_\ell^m(x) \equiv N_\ell^m P_\ell^m(x)
$$

using numbers of type `T`.

See also [`Plm`](@ref) and [`λlm`](@ref).
