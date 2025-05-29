```
GridLoad(γ=GridSpec(); ID=:default, option=:minimal)
```

  * `γ.path` にあるファイルから読み込まれたグリッド変数の `NamedTuple` を返します（`?GridSpec` を参照）。
  * option : 

      * option=:minimal（デフォルト）でグリッドセルの中心位置（XC, YC）のみを取得します。
      * option=:light で2Dグリッド変数の完全なセットを取得します。
      * option=:full で2Dおよび3Dグリッド変数の完全なセットを取得します。

MITgcmの命名規則に基づくグリッド変数は次のとおりです：

  * XC, XG, YC, YG, AngleCS, AngleSN, hFacC, hFacS, hFacW, Depth.
  * RAC, RAW, RAS, RAZ, DXC, DXG, DYC, DYG.
  * DRC, DRF, RC, RF（一次元）

MITgcmのドキュメント：

https://mitgcm.readthedocs.io/en/latest/algorithm/algorithm.html#spatial-discretization-of-the-dynamical-equations

```jldoctest; output = false
using MeshArrays
γ = GridSpec(ID=:LLC90)
Γ = GridLoad(γ;option="full")

isa(Γ.XC,MeshArray)

# output

true
```
