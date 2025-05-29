```julia
struct DipoleScatteringModel{T<:Number} <: ScatteringOptics.AbstractScatteringModel
```

薄いスクリーン近似に基づく異方性散乱モデル。この散乱モデルは、Psaltis et al. 2018で説明された双極子場の特性を採用しています。

** コンストラクタのキーワード ** デフォルトの数値は、Johnson et al. 2018で提示された最適フィットパラメータに基づいています。

  * `α::Number`: 位相変動のべき法則指数（コルモゴロフは5/3）。
  * `rin_cm::Number`: cm単位の散乱スクリーンの内スケール。
  * `θmaj_mas::Number`: 指定された参照波長での主軸の角度広がりのFWHM（ミリアーク秒単位）。
  * `θmin_nas::Number`: 指定された参照波長での副軸の角度広がりのFWHM（ミリアーク秒単位）。
  * `ϕ_deg::Number`: 散乱の主軸の位置角（度単位）。
  * `λ0_cm::Number`: cm単位の散乱モデルの参照波長。
  * `D_kpc::Number`: 観測者から散乱スクリーンまでの距離（kpc単位）。
  * `R_kpc::Number`: ソースから散乱スクリーンまでの距離（kpc単位）。
