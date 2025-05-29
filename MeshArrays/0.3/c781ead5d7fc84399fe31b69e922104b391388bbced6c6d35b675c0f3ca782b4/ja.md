```
GridLoadVar(nam::String,γ::gcmgrid)
```

`γ.path`にあるファイルから読み込まれたグリッド変数を返します（`?GridSpec`、`?GridLoad`を参照）。

MITgcmの命名規則に基づくグリッド変数は次のとおりです：

  * XC, XG, YC, YG, AngleCS, AngleSN, hFacC, hFacS, hFacW, Depth.
  * RAC, RAW, RAS, RAZ, DXC, DXG, DYC, DYG.
  * DRC, DRF, RC, RF（一次元）

MITgcmのドキュメント：

https://mitgcm.readthedocs.io/en/latest/algorithm/algorithm.html#spatial-discretization-of-the-dynamical-equations

```jldoctest; output = false
using MeshArrays

γ = GridSpec("CubeSphere",MeshArrays.GRID_CS32)
XC = GridLoadVar("XC",γ)

isa(XC,MeshArray)

# output

true
```
