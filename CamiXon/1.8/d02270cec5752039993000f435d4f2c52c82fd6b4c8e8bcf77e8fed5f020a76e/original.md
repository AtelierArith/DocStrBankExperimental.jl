```
RH1s(Z::Int, r::T) where T <:Real
```

Analytic expression for the *hydrogenic* 1s radial wavefunction and its derivative in the format $Z = \tilde{R} + i \tilde{R}^′$, where

$$
    \tilde{R}_{1s}(ρ) = Z^{3/2} 2 e^{-Zρ}
$$

is the radial wavefunction and

$$
    \tilde{R}^′_{1s}(ρ) = -Z^{5/2} 2 e^{-Zρ}
$$

its derivative, with $ρ$ the radial distance to the nucleus in a.u..

#### Example:

```
atom = castAtom(Z=1, A=1, Q=0; msg=false);
orbit = castSpinorbit(n=1, ℓ=0; msg=false);
grid = autoGrid(atom, spinorbit, Float64; Nboost=1, msg=false);
def = castDef(grid, atom, spinorbit, codata);

RH1s_example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N];

plot_wavefunction(RH1s_example, 1:grid.N, grid, def; reduced=false)
```

The plot is made using `CairomMakie`. NB.: `plot_function` is not included in the `CamiXon` package. ![Image](../../assets/RH1s.png)
