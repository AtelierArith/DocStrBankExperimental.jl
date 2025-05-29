```
UFk(k::Int, P::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

$k^{th}$-order-multipole contribution to the *direct* screening potential  by an electron in the (reduced) radial wavefunction `P` of an atom.

$$
U_{F}^{k}(\rho)
=\frac{1}{\rho^{k+1}}\int_{0}^{\rho}\varrho^{k}
\left[\tilde{R}_{nl}(\varrho)\right]^{2}
\varrho^{2}d\varrho+\rho^{k}\int_{\rho}^{\infty}
\frac{1}{\varrho^{k+1}}
\left[\tilde{R}_{nl}(\varrho)\right]^{2}\varrho^{2}d\varrho.
$$

#### Example:

```
codata = castCodata(2022)
atom = castAtom(Z=2, A=4, Q=0; msg=false);
orbit = castOrbit(n=1, ℓ=0; msg=false);
grid = autoGrid(atom, orbit, Float64; msg=true);
def = castDef(grid, atom, orbit, codata);
E = 0;
scr = zeros(grid.T,grid.N);       
def, adams, inE, Z = adams_moulton_nodes(E, scr, grid, def; imax=100, msg=false);
def, adams, inE, Z = adams_moulton_iterate!(Z, inE, grid, def, adams; imax=25, ϵ=1e-10, msg=false);
P1 = real(Z);
UF0P1 = UF(0, P1, grid);
plot_function(scrUF0P1, 1:grid.N, grid; title="He4(1s,1s):  direct screening potential")
```

The plot is made using `CairomMakie`. NB.: `plot_function` is not included in the `CamiXon` package. ![Image](../assets/He41s-UF0.png)
