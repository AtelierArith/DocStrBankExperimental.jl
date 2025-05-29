```
silvera_goldman_singlet(r::T) where T<:Real
```

Parametrization in *Hartree* a.u. of the singlet $(^{1}\Sigma_{g}^{+})$ potential of $\mathrm{H}_{2}$ (Eh = 219474.6 cm-1), 

$$
   V_{s}(r)=V_{t}(r)-J(r)
$$

where $V_{t}$ is the triplet potential ([`silvera_goldman_triplet`](@ref)) and $J(r)$ is the exchange contribution ([`silvera_goldman_triplet`](@ref)).
