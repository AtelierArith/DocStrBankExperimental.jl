```
hydrogenic_reduced_wavefunction(atom::Atom, spinorbit::Spinorbit, grid::CamiDiff.Grid{T}) where T<:Real
```

Analytic expression for the hydrogenic wavefunction written in the format $Z = \tilde{χ} + i \tilde{χ}^′$, where $\tilde{χ}_{nℓ}(ρ)$ is the *reduced* radial wavefunction and $\tilde{χ}^′_{nℓ}(ρ)$ its derivative, with $ρ$ the radial distance to the nucleus in a.u.. The expression is evaluated for a given [`Atom`](@ref) in a given [`Orbit`](@ref) on a given [`CamiDiff.Grid`](@extref). The argument [`Def`](@ref) completes the definition of the problem.

$$
    \tilde{\chi}_{nl}(\rho)
    =\mathcal{N}_{nl}^{-1/2}(2Z/n)^{l+3/2}\rho^{l+1}e^{-Zρ/n}
    L_{n-l-1}^{2l+1}(2Z\rho/n)
$$

where $L_{n-l-1}^{2l+1}(2Z\rho/n)$ is the generalized Laguerre polynomial `CamiMath.generalized_laguerreL` and

$$
    \mathcal{N}_{nl}
    = {\displaystyle \int\nolimits _{0}^{\infty}}x^{2l+2}e^{-x}
    \left[L_{n-l-1}^{2l+1}(x)\right]^{2}dx
    = \frac{2n\Gamma(n+l+1)}{\Gamma(n-l)}
$$

is the norm of the wavefunction.

#### Example:

```
julia> codata = castCodata(2022);

julia> atom = castAtom(;Z=1, A=1, Q=0, msg=false);

julia> spinorbit = castSpinorbit(n=25, ℓ=10);

julia> grid = autoGrid(atom, spinorbit, Float64; msg=true);
CamiDiff.Grid created: exponential, Float64, rmax = 3651.58 a.u., N = 1320, h = 0.0075815, r0 = 0.164537

julia> Z = hydrogenic_reduced_wavefunction(atom, spinorbit, grid);
 IOP capture at generalized_laguerre_polynom(35, 21): output converted to BigInt

julia> def = castDef(grid, atom, spinorbit, codata; msg=true);
Def created for ¹H:25n on exponential grid of 1320 points

plot_wavefunction(Z, 1:grid.N, grid, def)
```

The plot is made using `CairomMakie`. NB.: `plot_wavefunction` is not included in the `CamiXon` package. ![Image](../../assets/H1_25n.svg)
