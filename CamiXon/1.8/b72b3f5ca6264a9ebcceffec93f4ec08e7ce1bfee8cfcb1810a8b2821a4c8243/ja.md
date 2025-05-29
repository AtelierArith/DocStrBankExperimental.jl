```
UFk(k::Int, P::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

$$
k^{th}
$$

-次数の多極子寄与を*直接*スクリーニングポテンシャルとして、原子の（縮小された）放射状波動関数 `P` によって電子によって与えられます。

$$
U_{F}^{k}(\rho)
=\frac{1}{\rho^{k+1}}\int_{0}^{\rho}\varrho^{k}
\left[\tilde{R}_{nl}(\varrho)\right]^{2}
\varrho^{2}d\varrho+\rho^{k}\int_{\rho}^{\infty}
\frac{1}{\varrho^{k+1}}
\left[\tilde{R}_{nl}(\varrho)\right]^{2}\varrho^{2}d\varrho.
$$

#### 例:

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

プロットは `CairomMakie` を使用して作成されます。注: `plot_function` は `CamiXon` パッケージには含まれていません。 ![Image](../assets/He41s-UF0.png)
