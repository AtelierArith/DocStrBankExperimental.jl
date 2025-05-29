```
specificationplot([S,CS,T], [WS,WU,WT])
```

This function visualizes the control synthesis using the [`hinfsynthesize`](@ref) with the three weighting functions $W_S(s), W_U(s), W_T(s)$ inverted and scaled by γ, against the corresponding transfer functions $S(s), C(s)S(s), T(s)$, to verify visually that the specifications are met. This may be run using both MIMO and SISO systems.

# Keyword args

  * `wint`: `(-3, 5)` frequency range (log10)
  * `wnum`: 201 number of frequency points
  * `hz`: true
  * `nsigma`: typemax(Int) number of singular values to show
  * `s_labels`: `[   "σ(S)",   "σ(CS)",   "σ(T)",

]`

  * `w_labels`: `[   "γ σ(Wₛ⁻¹)",   "γ σ(Wᵤ⁻¹)",   "γ σ(Wₜ⁻¹)",

]`

  * `colors`: `[:blue, :red, :green]` colors for $S$, $CS$ and $T$
