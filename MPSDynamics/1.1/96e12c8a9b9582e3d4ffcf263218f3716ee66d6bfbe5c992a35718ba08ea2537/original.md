```
protontransfermpo(ω0e,ω0k,x0e,x0k, Δ, dRC, d, N, chainparams, RCparams, λreorg)
```

Generate a MPO for a system described in space with a reaction coordinate (RC) tensor. The Hamiltonian of the two-level system and of the reaction coordinate tensor reads 

$H_S + H_{RC} + H_{int}^{S-RC} = \omega^0_{e} |e\rangle \langle e| + \omega^0_{k} |k\rangle \langle k| + \Delta (|e\rangle \langle k| + |k\rangle \langle e|) + \omega_{RC} (d^{\dagger}d + \frac{1}{2}) + g_{e} |e\rangle \langle e|( d + d^{\dagger})+ g_{k} |k \rangle \langle k|( d + d^{\dagger})$ The RC tensor is coupled to a bosonic bath, taking into account the induced reorganization energy $H_B + H_{int}^{RC-B} = \int_{-∞}^{+∞} dk ω_k b_k^\dagger b_k - (d + d^{\dagger})\int_0^∞ dω\sqrt{J(ω)}(b_ω^\dagger+b_ω) + \lambda_{reorg}(d + d^{\dagger})^2$ with $\lambda_{reorg} = \int \frac{J(\omega)}{\omega}d\omega.$

# Arguments

  * `ω0e`: enol energy at reaction coordinate value x=0
  * `ω0k`: keto energy at reaction coordinate value x=0
  * `x0e`: enol equilibrium displacement
  * `x0k`: keto equilibrium displacement
  * `Δ`: direct coupling between enol and keto
  * `dRC`: fock space of the RC tensor
  * `d`: number of Fock states of the chain modes
  * `N`: length of the bosonic chain
  * `chainparams`: chain parameters, of the form `chainparams`=$[[ϵ_0,ϵ_1,...],[t_0,t_1,...],c_0]$, can be chosen to represent any arbitrary spectral density $J(ω)$ at any temperature.
  * `RCparams`: RC tensor parameter, of the form `RCparams`=$[ω_RC,-g/x]$
  * `λreorg`: reorganization energy
