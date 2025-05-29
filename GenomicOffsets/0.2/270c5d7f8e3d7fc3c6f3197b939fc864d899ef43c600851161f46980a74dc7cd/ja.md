```
LFMM_Ftest(model::LFMM, Y::AbstractMatrix{T1}, X::AbstractMatrix{T2}; genomic_control::Bool=true, center=true) where {T1<:Real,T2<:Real}
```

線形固定効果混合モデル (LFMM) の F-統計量 (F-test) を計算します。TODO: 参照と説明を追加。

# 引数

  * `model`: `RidgeLFMM` から得られた `LFMM{T<:Real}` データ構造。
  * `Y`: サイズ NxL の中心化された遺伝子型行列。
  * `X`: サイズ NxP の中心化された環境行列。
  * `genomic_control`: true の場合、F-統計量にゲノムコントロールを適用します。
  * `center`: true の場合、遺伝子型行列と環境行列の両方が中心化されます。false の場合、両方の行列は中心化されていると見なされます。

# 戻り値

  * 遺伝子型行列のローカスに対する p 値のベクトル。
