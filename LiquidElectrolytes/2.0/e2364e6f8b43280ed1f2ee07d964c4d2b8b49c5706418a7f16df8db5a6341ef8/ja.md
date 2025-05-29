```
chemical_potentials!(μ,u,electrolyte)
```

濃度から化学ポテンシャルを計算します。

入力:

  * `μ`: 結果のメモリ（埋められます）
  * `u`: 局所的な解ベクトル（濃度、ポテンシャル、圧力）

返り値 `μ0, μ`: 溶媒の化学ポテンシャルとイオンの化学ポテンシャル。

```jldoctest
using LessUnitful
ely = ElectrolyteData(c_bulk = fill(0.01ufac"mol/dm^3", 2))
μ0, μ = chemical_potentials!([0.0, 0.0], vcat(ely.c_bulk, [0, 0]), ely)
round(μ0, sigdigits = 5), round.(μ, sigdigits = 5)
# output

(-0.89834, [-21359.0, -21359.0])
```

!!! note "v0.2 と v0.3 の間の破壊的変更"
    この関数はバージョン0.3で修正されました。以前はイオンの化学ポテンシャルを計算するためにモル体積 $v$ を使用していましたが、効果的なモル体積 $\bar v = v + κv_0$ を使用するようになりました。κ=0の例には影響しません。

