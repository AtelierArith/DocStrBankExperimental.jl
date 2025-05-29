```
extinction_cross_section(axi::AxisymmetricTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

Calculate the extinction cross section per particle averaged over the uniform orientation distribution, according to Eq. (5.107) in Mishchenko et al. (2002).

$$
\left\langle C_{\text {ext }}\right\rangle=-\frac{2 \pi}{k_1^2} \operatorname{Re} \sum_{n=1}^{\infty} \sum_{m=0}^n\left(2-\delta_{m 0}\right)\left[T_{m n m n}^{11}(P)+T_{m n m n}^{22}(P)\right]
$$

Parameters:

  * `𝐓`: the T-Matrix of the scatterer.
  * `λ`: the wavelength of the incident wave in the host medium. Default to 2π.
