```
adams_moulton_solve!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}, adams::Adams1{T}) where T<:Real
```

Numerical solution of the 1D Schrödinger equation for the radial motion of a *valence* electron of energy `E`. Output: the improved `Adams` object, the energy convergence `ΔE`, and `Z`, where `P = real(Z)` is the *reduced* radial wavefunction and `Q = imag(Z)` its derivative.

#### Example:

```
atom = castAtom(Z=1, A=1, Q=0, msg=true)
orbit = castOrbit(n=1, ℓ=0)
grid = autoGrid(atom, orbit, Float64; Nboost=1, msg=true)
def = castDef(grid, atom, orbit, codata)
E = Ecal = convert(grid.T, bohrformula(atom.Z, orbit.n))
adams = castAdams(E, grid, def);

adams, ΔE, Z = adams_moulton_solve(E, grid, def, adams)
plot_wavefunction(Z, 1:grid.N, grid, def; reduced=true)
```

The plot is made using CairomMakie. NB.: `plot_wavefunction` is not part of the `CamiXon` package. ![Image](../../assets/hydrogen-1s-prepared.png)
