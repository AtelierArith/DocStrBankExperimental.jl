```
Transcorrelated1D(address; t=1.0, v=1.0, v_ho=0.0, cutoff=1, three_body_term=true)
```

Implements a transcorrelated Hamiltonian for contact interactions in one dimensional momentum space from [Jeszenski *et al.* (2018)](http://arxiv.org/abs/1806.11268). Currently limited to two component fermionic addresses.

$$
\begin{aligned}

\tilde{H} &= t \sum_{kσ}k^2 n_{k,σ} \\
    &\quad + \sum_{pqkσσ'} T_{pqk} a^†_{p-k,σ} a^†_{q+k,σ'} a_{q,σ'} a_{p,σ} \\
    &\quad + \sum_{pqskk'σσ'} Q_{kk'}a^†_{p-k,σ} a^†_{q+k,σ} a^†_{s+k-k',σ'}
                                       a_{s,σ'} a_{q,σ} a_{p,σ} \\
    &\quad + V̂_\mathrm{ho}
\end{aligned}
$$

where

$$
\begin{aligned}
\tilde{u}(k) &= \begin{cases} -\frac{2}{k^2} &\mathrm{if\ } |k| ≥ k_c\\
0 & \mathrm{otherwise}
\end{cases}
\\

T_{pqk} &= \frac{v}{M} + \frac{2v}{M}\left[k^2\tilde{u}(k)
          - (p - q)k\tilde{u}(k)\right] + \frac{2v^2}{t}W(k)\\
W(k) &= \frac{1}{M^2}\sum_{q} (k - q)q\, \tilde{u}(q)\,\tilde{u}(k - q) \\
Q_{kl} &= -\frac{v^2}{t M^2}k \tilde{u}(k)\,l\tilde{u}(l),
\end{aligned}
$$

# Arguments

  * `address`: The starting address, defines number of particles and sites.
  * `v`: The interaction parameter.
  * `t`: The kinetic energy prefactor.
  * `v_ho`: Strength of the external harmonic oscillator potential $V̂_\mathrm{ho}$. See [`HubbardMom1DEP`](@ref).
  * `cutoff` controls $k_c$ in equations above. Note: skipping generating off-diagonal elements below the cutoff is not implemented - zero-valued elements are returned instead.
  * `three_body_term`: If set to false, generating three body excitations is skipped. Note: when disabling three body terms, cutoff should be set to a higher value for best results.

# See also

  * [`HubbardMom1D`](@ref)
  * [`HubbardMom1DEP`](@ref)
