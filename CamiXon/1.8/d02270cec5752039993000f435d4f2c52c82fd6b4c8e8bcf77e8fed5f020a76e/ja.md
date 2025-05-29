```
RH1s(Z::Int, r::T) where T <:Real
```

水素様の1s放射波動関数とその導関数の解析的表現は、$Z = \tilde{R} + i \tilde{R}^′$の形式で表されます。ここで、

$$
    \tilde{R}_{1s}(ρ) = Z^{3/2} 2 e^{-Zρ}
$$

は放射波動関数であり、

$$
    \tilde{R}^′_{1s}(ρ) = -Z^{5/2} 2 e^{-Zρ}
$$

はその導関数で、$ρ$は原子核までの距離（原子単位）です。

#### 例:

```
atom = castAtom(Z=1, A=1, Q=0; msg=false);
orbit = castSpinorbit(n=1, ℓ=0; msg=false);
grid = autoGrid(atom, spinorbit, Float64; Nboost=1, msg=false);
def = castDef(grid, atom, spinorbit, codata);

RH1s_example = [RH1s(atom.Z, grid.r[n]) for n=1:grid.N];

plot_wavefunction(RH1s_example, 1:grid.N, grid, def; reduced=false)
```

プロットは`CairomMakie`を使用して作成されます。注：`plot_function`は`CamiXon`パッケージには含まれていません。 ![Image](../../assets/RH1s.png)
