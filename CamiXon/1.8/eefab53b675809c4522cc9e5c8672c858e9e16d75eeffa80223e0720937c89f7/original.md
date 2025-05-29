```
reduce_wavefunction(Z::Vector{Complex{T}}, grid::CamiDiff.Grid{T}) where T<:Real
```

Conversion from the *ordinary* radial wavefunction $\tilde{R}_{nl}(ρ)$ to the *reduced* radial wavefuntion

$$
    \tilde{\chi}_{nl}(ρ) = ρ \tilde{R}_{nl}(ρ).
$$

where $ρ$ is the radial distance to the nucleus in a.u..

#### Example:

```
julia> atom = castAtom(Z=1, A=1, Q=0; msg=false);
julia> spinorbit = castSpinorbit(n=1, ℓ=0; msg=false);
julia> grid = autoGrid(atom, spinorbit, Float64);
julia> RH1s_example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N];
julia> ZH1s_example = reduce_wavefunction(RH1s_example, grid);
julia> ZH1s_generic = hydrogenic_reduced_wavefunction(atom, spinorbit, grid);
julia> @test ZH1s_example ≈ ZH1s_generic
Test Passed

julia> f1 = real(ZH1s_example);
julia> f2 = real(ZH1s_generic);
julia> compare_functions(f1, f2, 1:grid.N, grid)
```

The plot is made using `CairomMakie`. NB.: `compare_functions` is not included in the `CamiXon` package. ![Image](../../assets/compareXH1s.png) ```
