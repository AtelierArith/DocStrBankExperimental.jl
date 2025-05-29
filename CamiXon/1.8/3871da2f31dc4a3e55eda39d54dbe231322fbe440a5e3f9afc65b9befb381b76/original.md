```
RH2s(Z::Int, r::T) where T <:Real
```

Analytic expression for the *hydrogenic* 1s reduced radial wavefunction and its derivative in the format $Z = \tilde{R} + i \tilde{R}^′$, where

$$
    \tilde{R}_{2s}(ρ)=\left(Z/2\right)^{3/2}(1-Zρ/2)2e^{-Zρ/2}
$$

is the radial wavefunction and

$$
    \tilde{R}_{2s}(ρ)=-\left(Z/2\right)^{5/2}(2-Zρ/2)2e^{-Zρ/2}
$$

its derivative, with $ρ$ the radial distance to the nucleus in a.u..

#### Example:

```
atom = castAtom(Z=1, A=1, Q=0; msg=false);
orbit = castSpinorbit(n=2, ℓ=0; msg=false);
grid = autoGrid(atom, spinorbit, Float64; Nboost=1, msg=false);
def = castDef(grid, atom, spinorbit, codata; msg=false);

RH2s_example = [RH2s(atom.Z, grid.r[n]) for n=1:grid.N];

plot_wavefunction(RH2s_example, 1:grid.N, grid, def; reduced=false)
```

The plot is made using `CairomMakie`. NB.: `plot_wavefunction` is not included in the `CamiXon` package. ![Image](../../assets/RH2s.png)
