```
GaussianKernel <: AbstractKernel
GaussianKernel([ℓ/Δx])
```

Represents a truncated Gaussian spreading kernel.

# Definition

$$
ϕ(x) = e^{-x² / 2ℓ²}
$$

where $ℓ$ is the characteristic width of the kernel.

# Fourier transform

$$
ϕ̂(k) = \sqrt{2πℓ²} e^{-ℓ² k² / 2}
$$

# Parameter selection

By default, given a kernel half-width $M$, an oversampling factor $σ$ and the oversampling grid spacing $Δx$, the characteristic width $ℓ$ is chosen as [1]

$$
ℓ² = Δx² \frac{σ}{2σ - 1} \frac{M}{π}
$$

This default value can be overriden by explicitly passing a value of the wanted normalised width $ℓ/Δx$.

# Implementation details

In the implementation, this kernel is efficiently evaluated using the fast Gaussian gridding method proposed by Greengard & Lee [2].

[1] Potts & Steidl, SIAM J. Sci. Comput. **24**, 2013 (2003) 
[2] Greengard & Lee, SIAM Rev. **46**, 443 (2004)
