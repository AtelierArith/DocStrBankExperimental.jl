```
restore_wavefunction(Z::Vector{Complex{T}}, atom::Atom, spinorbit::Spinorbit, grid::CamiDiff.Grid{T}) where T<:Real
```

Conversion from the *reduced* radial wavefunction $\tilde{\chi}_{nl}(ρ)$ to the *ordinary* radial wavefuntion $\tilde{R}_{nl}(ρ)$,

$$
    \tilde{R}_{nl}(ρ)=\tilde{\chi}_{nl}(ρ)/ρ,
$$

where $ρ$ is the radial distance to the nucleus in a.u..

#### Example:

``` julia> atom = castAtom(Z=1, A=1, Q=0; msg=false); julia> spinorbit = castSpinorbit(n=1, ℓ=0; msg=false); julia> grid = autoGrid(atom, spinorbit, Float64); julia> RH1s*example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N]; julia> ZH1s*example = reduce*wavefunction(RH1s*example, grid); julia> RH1s*generic = restore*wavefunction(ZH1s_generic, atom, spinorbit, grid);  

julia> @test RH1s*example ≈ RH1s*generic  Test Passed
