```
scattering_cross_section(axi::AxisymmetricTransitionMatrix{CT, N}, λ=2π) where {CT, N}
```

Calculate the scattering cross section per particle averaged over the uniform orientation distribution, according to Eq. (5.141) in Mishchenko et al. (2002).

$$
\left\langle C_{\text {sca }}\right\rangle=\frac{2 \pi}{k_1^2} \sum_{n=1}^{\infty} \sum_{n^{\prime}=1}^{\infty} \sum_{m=0}^{\min \left(n, n^{\prime}\right)} \sum_{k=1}^2 \sum_{l=1}^2\left(2-\delta_{m 0}\right)\left|T_{m n m n^{\prime}}^{k l}(P)\right|^2
$$

Parameters:

  * `𝐓`: the T-Matrix of the scatterer.
  * `λ`: the wavelength of the incident wave in the host medium. Default to 2π.
