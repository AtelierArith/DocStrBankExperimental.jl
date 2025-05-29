```
RH2s(Z::Int, r::T) where T <:Real
```

*水素様* 1s 縮小放射波動関数とその導関数の解析的表現は、$Z = \tilde{R} + i \tilde{R}^′$ の形式であり、ここで

$$
    \tilde{R}_{2s}(ρ)=\left(Z/2\right)^{3/2}(1-Zρ/2)2e^{-Zρ/2}
$$

は放射波動関数であり、

$$
    \tilde{R}_{2s}(ρ)=-\left(Z/2\right)^{5/2}(2-Zρ/2)2e^{-Zρ/2}
$$

はその導関数であり、$ρ$ は原子核までの放射距離（a.u.単位）です。

#### 例:

```
atom = castAtom(Z=1, A=1, Q=0; msg=false);
orbit = castSpinorbit(n=2, ℓ=0; msg=false);
grid = autoGrid(atom, spinorbit, Float64; Nboost=1, msg=false);
def = castDef(grid, atom, spinorbit, codata; msg=false);

RH2s_example = [RH2s(atom.Z, grid.r[n]) for n=1:grid.N];

plot_wavefunction(RH2s_example, 1:grid.N, grid, def; reduced=false)
```

プロットは `CairomMakie` を使用して作成されます。注意：`plot_wavefunction` は `CamiXon` パッケージには含まれていません。 ![Image](../../assets/RH2s.png)
