```
silvera_goldman_potential(grid::CamiDiff.Grid{T}; S=0) where T<:Real
```

CamiDiff.Grid の *Hartree* a.u. における $\mathrm{H}_{2}$ の一重項 (S=0) および三重項 (S=1) ポテンシャルの表現、

$$
    \mathcal{V}(r)=V_{D}(r)+J(r)\mathbf{s}_{1}\cdot\mathbf{s}_{2},
$$

ここで $\mathbf{S} = \mathbf{s}_{1}+\mathbf{s}_{2}$ であり、

$$
    V_{D}(r)=\frac{1}{4}[V_{s}(r)+3V_{t}(r)] \ \mathrm{and}\ J(r)=V_{t}(r)-V_{s}(r)
$$

はそれぞれ直接項と交換項として知られています； $V_{s}:$ [`silvera_goldman_singlet`](@ref) を参照、 $V_{t}:$ [`silvera_goldman_triplet`](@ref) を参照、 $J(r):$ [`silvera_goldman_exchange`](@ref) を参照。

I.F. Silvera, - Rev. Mod. Phys., 52, 393 (1980) を参照してください。
