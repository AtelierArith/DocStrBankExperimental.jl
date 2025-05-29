```
restore_wavefunction(Z::Vector{Complex{T}}, atom::Atom, spinorbit::Spinorbit, grid::CamiDiff.Grid{T}) where T<:Real
```

*縮小された* 放射状波動関数 $\tilde{\chi}_{nl}(ρ)$ から *通常の* 放射状波動関数 $\tilde{R}_{nl}(ρ)$ への変換、

$$
    \tilde{R}_{nl}(ρ)=\tilde{\chi}_{nl}(ρ)/ρ,
$$

ここで $ρ$ は原子核までの放射状距離（a.u.単位）です。

#### 例:

```julia> atom = castAtom(Z=1, A=1, Q=0; msg=false); julia> spinorbit = castSpinorbit(n=1, ℓ=0; msg=false); julia> grid = autoGrid(atom, spinorbit, Float64); julia> RH1s*example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N]; julia> ZH1s*example = reduce*wavefunction(RH1s*example, grid); julia> RH1s*generic = restore*wavefunction(ZH1s_generic, atom, spinorbit, grid);

julia> @test RH1s*example ≈ RH1s*generic  Test Passed
```
