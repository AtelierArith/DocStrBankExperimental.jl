```
UGk(k::Int, P1::Vector{T}, P2::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

$k^{th}$-order-multipole contribution to the *exchange* screening potential  of the (reduced) electronic wavefunctions `P1` and `P2` of the same atom.

$$
U_{G}^{k}(\rho)
=\frac{1}{\rho^{k+1}}\int_{0}^{\rho}\varrho^{k}\tilde{R}_{nl}(\varrho)
\tilde{R}_{n^{\prime}l^{\prime}}(\varrho)\,
\varrho^{2}d\varrho+\rho^{k}\int_{\rho}^{\infty}
\frac{1}{\varrho^{k+1}}\tilde{R}_{nl}(\varrho)
\tilde{R}_{n^{\prime}l^{\prime}}(\varrho)\,\varrho^{2}d\varrho.
$$

#### Example:

```
atom = castAtom(Z=2, A=4, Q=0; msg=true)
orbit1 = castOrbit(n=1, ℓ=0; msg=true)
orbit2 = castOrbit(n=2, ℓ=0; msg=true)
scr = nothing
grid = autoGrid(atom, [orbit1,orbit2], Float64; Nboost=1, msg=true)
def1 = castDef(grid, atom, spinorbit1, codata; scr)
E = inEE(def1)
adams = castAdams(E, grid, def1)
E, def, adams, Z1 = adams_moulton_master(E, grid, def1, adams; Δν=Value(1,"kHz"), imax=50, msg=false);

def2 = castDef(grid, atom, spinorbit2, codata; scr)
E = inEE(def2)
adams = castAdams(E, grid, def2)
E, def, adams, Z2 = adams_moulton_master(E, grid, def2, adams; Δν=Value(1,"kHz"), imax=50, msg=false);

P1 = real(Z1);
P2 = real(Z2);

UG0 = UG(0, P1, P2, grid);
plot_function(UG0, 1:grid.N, grid; title="He4(1s,2s):  exchange screening potential")
```

The plot is made using `CairomMakie`. NB.: `plot_function` is not included in the `CamiXon` package. ![Image](../assets/He41s-UG0.png)
