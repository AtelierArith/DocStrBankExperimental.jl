```julia
ChevalierMarco()
ChevalierMarco()

```

# Model:

$$
W = \int\limits_{3}^{I_1(\vec\lambda)} \exp\bigg(\sum\limits_{i=0}^{N}a_i(I_1-3)^i\bigg)\text{d}I_1+ \int\limits_{3}^{I_2(\vec\lambda)} \sum\limits_{i=0}^{n}\frac{b_i}{I_2^i}\text{d}I_2
$$

$$
[\mathbf{S}] = 2(I-\frac{\partial W}{\partial I_1} - C^{-2}\frac{\partial W}{\partial I_2})
$$

$$
[\mathbf{\sigma}] = \mathbf{F} \cdot \mathbf{S}
$$

# Parameters:

  * `a⃗`
  * `b⃗`

Note:

  * Model is not compatible with AD. A method for accessing the Second Piola Kirchoff Tensor and Cauchy Stress Tensor have been implemented.

> Chevalier L, Marco Y. Tools for multiaxial validation of behavior laws chosen for modeling hyper‐elasticity of rubber‐like materials. Polymer Engineering & Science. 2002 Feb;42(2):280-98.

