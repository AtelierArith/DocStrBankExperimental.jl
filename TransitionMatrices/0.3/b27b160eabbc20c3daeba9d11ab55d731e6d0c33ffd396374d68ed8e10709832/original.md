```
scattering_cross_section(𝐓::AbstractTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

Calculate the scattering cross section per particle averaged over the uniform orientation distribution, according to Eq. (5.140) in Mishchenko et al. (2002).

$$
\left\langle C_{\mathrm{sca}}\right\rangle=\frac{2 \pi}{k_1^2} \sum_{n=1}^{\infty} \sum_{m=-n}^n \sum_{n^{\prime}=1}^{\infty} \sum_{m^{\prime}=-n^{\prime}}^{n^{\prime}} \sum_{k=1}^2 \sum_{l=1}^2\left|T_{m n m^{\prime} n^{\prime}}^{k l}(P)\right|^2
$$

Parameters:

  * `𝐓`: the T-Matrix of the scatterer.
  * `λ`: the wavelength of the incident wave in the host medium. Default to 2π.
