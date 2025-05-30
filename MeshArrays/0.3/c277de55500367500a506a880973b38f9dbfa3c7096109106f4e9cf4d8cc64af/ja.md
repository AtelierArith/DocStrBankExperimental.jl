```
GridLoad(γ=GridSpec(); ID=:default, option=:minimal)
```

  * `γ.path` にあるファイルから読み込まれたグリッド変数の `NamedTuple` を返します（`?GridSpec` を参照）。
  * option : 

      * (デフォルト) option=:minimal は、グリッドセルの中心位置 (XC, YC) のみが読み込まれることを意味します。
      * option=:full は、2D グリッド変数の完全なセットを提供します。
      * option=:full は、2D および 3D グリッド変数の完全なセットを提供します。

MITgcm の命名規則に基づくグリッド変数は次のとおりです：

  * XC, XG, YC, YG, AngleCS, AngleSN, hFacC, hFacS, hFacW, Depth.
  * RAC, RAW, RAS, RAZ, DXC, DXG, DYC, DYG.
  * DRC, DRF, RC, RF (一次元)

MITgcm ドキュメント : 

https://mitgcm.readthedocs.io/en/latest/algorithm/algorithm.html#spatial-discretization-of-the-dynamical-equations

```jldoctest; output = false
using MeshArrays
γ = GridSpec(ID=:LLC90)
Γ = GridLoad(γ;option="full")

isa(Γ.XC,MeshArray)

# output

true
```
