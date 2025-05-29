```
BosonBath(op, η_real, γ_real, η_imag, γ_imag, δ=0.0; combine=true)
```

Generate BosonBath object for the case where the correlation function splits into real part and imaginary part.

$$
\begin{aligned}
C(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega)\left[n(\omega)e^{i\omega \tau}+(n(\omega)+1)e^{-i\omega \tau}\right]\\
&=\sum_i \eta_i \exp(-\gamma_i \tau),
\end{aligned}
$$

where $J(\omega)$ is the spectral density of the bath and $n(\omega)$ represents the Bose-Einstein distribution.

When $\gamma_i \neq \gamma_i^*$, a closed form for the HEOM can be obtained by further decomposing $C(\tau)$ into its real (R) and imaginary (I) parts as

$$
C(\tau)=\sum_{u=\textrm{R},\textrm{I}}(\delta_{u, \textrm{R}} + i\delta_{u, \textrm{I}})C^{u}(\tau)
$$

where $\delta$ is the Kronecker delta function and $C^{u}(\tau)=\sum_i \eta_i^u \exp(-\gamma_i^u \tau)$

# Parameters

  * `op::QuantumObject` : The system coupling operator, must be Hermitian and, for fermionic systems, even-parity to be compatible with charge conservation.
  * `η_real::Vector{Ti<:Number}` : the coefficients $\eta_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
  * `γ_real::Vector{Tj<:Number}` : the coefficients $\gamma_i$ in real part of bath correlation function $C^{u=\textrm{R}}$.
  * `η_imag::Vector{Tk<:Number}` : the coefficients $\eta_i$ in imaginary part of bath correlation function $C^{u=\textrm{I}}$.
  * `γ_imag::Vector{Tl<:Number}` : the coefficients $\gamma_i$ in imaginary part of bath correlation function $C^{u=\textrm{I}}$.
  * `δ::Number` : The approximation discrepancy (Default to `0.0`) which is used for adding the terminator to HEOM matrix (see function: addTerminator)
  * `combine::Bool` : Whether to combine the exponential-expansion terms with the same frequency. Defaults to `true`.
