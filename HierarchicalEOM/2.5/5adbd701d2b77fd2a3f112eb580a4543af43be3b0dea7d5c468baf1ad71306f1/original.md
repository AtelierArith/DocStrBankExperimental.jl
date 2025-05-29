```
BosonBathRWA(op, η_absorb, γ_absorb, η_emit, γ_emit, δ=0.0)
```

A function for generating BosonBath object where the interaction between system and bosonic bath applies the rotating wave approximation (RWA).

$$
\begin{aligned}
C^{\nu=+}(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega) n(\omega) e^{i\omega \tau}\\
&=\sum_i \eta_i^{\nu=+} \exp(-\gamma_i^{\nu=+} \tau),\\
C^{\nu=-}(\tau)
&=\frac{1}{2\pi}\int_{0}^{\infty} d\omega J(\omega) (1+n(\omega)) e^{-i\omega \tau}\\
&=\sum_i \eta_i^{\nu=-} \exp(-\gamma_i^{\nu=-} \tau),
\end{aligned}
$$

where $\nu=+$ ($\nu=-$) represents absorption (emission) process, $J(\omega)$ is the spectral density of the bath and $n(\omega)$ is the Bose-Einstein distribution.

# Parameters

  * `op::QuantumObject` : The system annihilation operator according to the system-bosonic-bath interaction.
  * `η_absorb::Vector{Ti<:Number}` : the coefficients $\eta_i$ of absorption bath correlation function $C^{\nu=+}(\tau)$.
  * `γ_absorb::Vector{Tj<:Number}` : the coefficients $\gamma_i$ of absorption bath correlation function $C^{\nu=+}(\tau)$.
  * `η_emit::Vector{Tk<:Number}` : the coefficients $\eta_i$ of emission bath correlation function $C^{\nu=-}(\tau)$.
  * `γ_emit::Vector{Tl<:Number}` : the coefficients $\gamma_i$ of emission bath correlation function $C^{\nu=-}(\tau)$.
  * `δ::Number` : The approximation discrepancy (Defaults to `0.0`) which is used for adding the terminator to HEOMLS matrix (see function: addTerminator)
