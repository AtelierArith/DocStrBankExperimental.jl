```
BosonBath(op, η, γ, δ=0.0; combine=true)
```

Generate BosonBath object for the case where real part and imaginary part of the correlation function are combined.

$$
\begin{aligned}
C(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega)\left[n(\omega)e^{i\omega \tau}+(n(\omega)+1)e^{-i\omega \tau}\right]\\
&=\sum_i \eta_i \exp(-\gamma_i \tau),
\end{aligned}
$$

where $J(\omega)$ is the spectral density of the bath and $n(\omega)$ represents the Bose-Einstein distribution.

# Parameters

  * `op::QuantumObject` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `η::Vector{Ti<:Number}` : the coefficients $\eta_i$ in bath correlation function $C(\tau)$.
  * `γ::Vector{Tj<:Number}` : the coefficients $\gamma_i$ in bath correlation function $C(\tau)$.
  * `δ::Number` : The approximation discrepancy (Default to `0.0`) which is used for adding the terminator to HEOM matrix (see function: addTerminator)
  * `combine::Bool` : Whether to combine the exponential-expansion terms with the same frequency. Defaults to `true`.
