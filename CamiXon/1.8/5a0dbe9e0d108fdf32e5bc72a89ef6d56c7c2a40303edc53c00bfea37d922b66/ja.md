```
hydrogenic_reduced_wavefunction(atom::Atom, spinorbit::Spinorbit, grid::CamiDiff.Grid{T}) where T<:Real
```

水素様波動関数の解析的表現は、$Z = \tilde{χ} + i \tilde{χ}^′$の形式で書かれ、ここで$\tilde{χ}_{nℓ}(ρ)$は*縮小*放射状波動関数であり、$\tilde{χ}^′_{nℓ}(ρ)$はその導関数で、$ρ$は原子核までの放射距離（a.u.単位）です。この表現は、与えられた[`Atom`](@ref)に対して、与えられた[`Orbit`](@ref)上の、与えられた[`CamiDiff.Grid`](@extref)で評価されます。引数[`Def`](@ref)は問題の定義を完成させます。

$$
    \tilde{\chi}_{nl}(\rho)
    =\mathcal{N}_{nl}^{-1/2}(2Z/n)^{l+3/2}\rho^{l+1}e^{-Zρ/n}
    L_{n-l-1}^{2l+1}(2Z\rho/n)
$$

ここで、$L_{n-l-1}^{2l+1}(2Z\rho/n)$は一般化ラゲール多項式`CamiMath.generalized_laguerreL`であり、

$$
    \mathcal{N}_{nl}
    = {\displaystyle \int\nolimits _{0}^{\infty}}x^{2l+2}e^{-x}
    \left[L_{n-l-1}^{2l+1}(x)\right]^{2}dx
    = \frac{2n\Gamma(n+l+1)}{\Gamma(n-l)}
$$

は波動関数のノルムです。

#### 例:

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

プロットは`CairomMakie`を使用して作成されます。注意：`plot_wavefunction`は`CamiXon`パッケージには含まれていません。 ![Image](../../assets/H1_25n.svg)
