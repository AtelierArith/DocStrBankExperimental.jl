```
adams_moulton_solve!(Z::Vector{Complex{T}}, E::T, grid::CamiDiff.Grid{T}, def::Def{T}, adams::Adams1{T}) where T<:Real
```

エネルギー `E` の *価電子* の放射運動に対する1次元シュレーディンガー方程式の数値解。出力: 改良された `Adams` オブジェクト、エネルギー収束 `ΔE`、および `Z`。ここで、`P = real(Z)` は *縮小* 放射波動関数であり、`Q = imag(Z)` はその導関数です。

#### 例:

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

プロットはCairomMakieを使用して作成されます。注: `plot_wavefunction` は `CamiXon` パッケージの一部ではありません。 ![Image](../../assets/hydrogen-1s-prepared.png)
