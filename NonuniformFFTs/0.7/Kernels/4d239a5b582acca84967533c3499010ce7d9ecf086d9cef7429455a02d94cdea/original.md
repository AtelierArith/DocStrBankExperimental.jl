```
BackwardsKaiserBesselKernel <: AbstractKernel
BackwardsKaiserBesselKernel([β])
```

Represents a backwards [Kaiser–Bessel](https://en.wikipedia.org/wiki/Kaiser_window#Definition) (KB) spreading kernel.

This kernel basically results from swapping the [`KaiserBesselKernel`](@ref) spreading function and its Fourier transform. It has very similar properties to the Kaiser–Bessel kernel.

# Definition

$$
ϕ(x) = \frac{\sinh \left(β \sqrt{1 - x²} \right)}{π \sqrt{1 - x²}}
\quad \text{ for } |x| ≤ 1
$$

where $β$ is a shape factor.

# Fourier transform

$$
ϕ̂(k) = I₀ \left( \sqrt{β² - k²} \right)
$$

where $I₀$ is the zeroth-order [modified Bessel function](https://en.wikipedia.org/wiki/Modified_Bessel_function#Modified_Bessel_functions:_I%CE%B1,_K%CE%B1) of the first kind.

# Parameter selection

By default, the shape parameter is chosen to be [1]

$$
β = γ M π \left( 2 - \frac{1}{σ} \right)
$$

where $M$ is the kernel half-width and $σ$ the oversampling factor. Moreover, $γ = 0.995$ is an empirical "safety factor", similarly to the one used by FINUFFT [2], which slightly improves accuracy.

This default value can be overriden by explicitly passing a $β$ value.

# Implementation details

Since the evaluation of the hyperbolic sine functions can be costly, this kernel is efficiently evaluated via an accurate piecewise polynomial approximation. We use the same method originally proposed for FINUFFT [2] and later discussed by Shamshirgar et al. [3].

[1] Potts & Steidl, SIAM J. Sci. Comput. **24**, 2013 (2003) 
[2] Barnett, Magland & af Klinteberg, SIAM J. Sci. Comput. **41**, C479 (2019) 
[3] Shamshirgar, Bagge & Tornberg, J. Chem. Phys. **154**, 164109 (2021)
