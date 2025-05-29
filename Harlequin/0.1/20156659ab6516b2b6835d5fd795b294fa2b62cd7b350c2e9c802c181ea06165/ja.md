```
mutable struct NobsMatrixElement
```

この構造体は、マップ内のピクセルの条件行列をエンコードします。これは、KurkiSuonio2009の式(10)における行列M_pに相当しますが、以下のフィールドを実装しているため、強化されています。

  * `m`: 式(10)の3×3行列
  * `invm`: `m`の3×3逆行列
  * `invcond`: `m`の条件数*rcond*の逆数; このフィールドは、TOD内のサンプルと攻撃角がそのピクセルのI、Q、Uの一意の解を制約するのに十分かどうかを確認するのに役立ちます。
  * `neglected`: マップ作成中にピクセルがスキップされたかどうかを示すブールフラグ（通常、`invcond`が小さすぎる場合に発生します）

典型的な使用例は、[`update_nobs_matrix!`](@ref)を介して更新される`NobsMatrixElement`オブジェクトの配列で、以下の例のようになります。

```julia
NPIX = 10   # マップ内のピクセル数
nobs_matrix = [NobsMatrixElement() for i in 1:NPIX]

# 変数psi_angle、sigma_squared、pixidx、およびflagged
# はどこかで定義されている必要があります; それらはTODを含みます
update_nobs_matrix!(nobs_matrix, psi_angle, sigma_squared, pixidx, flagged)
```
