```
TreatmentTerm{T<:AbstractTreatment} <: AbstractTerm
```

治療および平行トレンドの仮定に関する仕様を含む用語です。詳細は[`treat`](@ref)を参照してください。

# フィールド

  * `sym::Symbol`: 治療状態を表すデータの列名。
  * `tr::T`: 興味のある因果パラメータを指定する治療タイプ。
  * `pr::P`: 平行トレンドの仮定を指定する平行タイプ。
