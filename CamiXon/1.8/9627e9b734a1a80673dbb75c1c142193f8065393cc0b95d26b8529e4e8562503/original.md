```
silvera_goldman_potential(grid::CamiDiff.Grid{T}; S=0) where T<:Real
```

CamiDiff.Grid representation in *Hartree* a.u. of the singlet (S=0) and triplet (S=1) potentials of $\mathrm{H}_{2}$,

$$
    \mathcal{V}(r)=V_{D}(r)+J(r)\mathbf{s}_{1}\cdot\mathbf{s}_{2},
$$

where $\mathbf{S} = \mathbf{s}_{1}+\mathbf{s}_{2}$ and 

$$
    V_{D}(r)=\frac{1}{4}[V_{s}(r)+3V_{t}(r)] \ \mathrm{and}\ J(r)=V_{t}(r)-V_{s}(r)
$$

are known as the direct and exchange contribution, respectively; $V_{s}:$ see [`silvera_goldman_singlet`](@ref),  $V_{t}:$ see [`silvera_goldman_triplet`](@ref), $J(r):$ see [`silvera_goldman_exchange`](@ref).

see I.F. Silvera, - Rev. Mod. Phys., 52, 393 (1980).
