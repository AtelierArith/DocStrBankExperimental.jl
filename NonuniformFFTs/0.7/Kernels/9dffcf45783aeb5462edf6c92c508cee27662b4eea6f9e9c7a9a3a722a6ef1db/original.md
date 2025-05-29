```
KaiserBesselKernel <: AbstractKernel
KaiserBesselKernel([β])
```

Represents a [Kaiser–Bessel](https://en.wikipedia.org/wiki/Kaiser_window#Definition) spreading kernel.

# Definition

$$
ϕ(x) = I₀ \left(β \sqrt{1 - x²} \right)
\quad \text{ for } |x| ≤ 1
$$

where $I₀$ is the zeroth-order [modified Bessel function](https://en.wikipedia.org/wiki/Modified_Bessel_function#Modified_Bessel_functions:_I%CE%B1,_K%CE%B1) of the first kind and $β$ is a shape factor.

# Fourier transform

$$
ϕ̂(k) = 2 \frac{\sinh\left( \sqrt{β² - k²} \right)}{\sqrt{β² - k²}}
$$

# Parameter selection

By default, the shape parameter is chosen to be [1]

$$
β = γ M π \left( 2 - \frac{1}{σ} \right)
$$

where $M$ is the kernel half-width and $σ$ the oversampling factor. Moreover, $γ = 0.980$ is an empirical "safety factor", similarly to the one used by FINUFFT [2], which slightly improves accuracy.

This default value can be overriden by explicitly passing a $β$ value.

# Implementation details

Since the evaluation of Bessel functions can be costly, this kernel is efficiently evaluated via an accurate piecewise polynomial approximation. We use the same method originally proposed for FINUFFT [2] and later discussed by Shamshirgar et al. [3].

[1] Potts & Steidl, SIAM J. Sci. Comput. **24**, 2013 (2003) 
[2] Barnett, Magland & af Klinteberg, SIAM J. Sci. Comput. **41**, C479 (2019) 
[3] Shamshirgar, Bagge & Tornberg, J. Chem. Phys. **154**, 164109 (2021)
