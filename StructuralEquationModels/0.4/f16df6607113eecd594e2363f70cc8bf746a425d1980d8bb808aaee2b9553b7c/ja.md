```
(1) replace_observed(model::AbstractSemSingle; kwargs...)

(2) replace_observed(model::AbstractSemSingle, observed; kwargs...)
```

観測された部分を入れ替えた新しいモデルを返します。

# 引数

  * `model::AbstractSemSingle`: 観測された部分を入れ替えるモデル。
  * `kwargs`: 追加のキーワード引数。通常は `data` と `specification` を含みます。
  * `observed`: `SemObserved` のサブタイプのオブジェクト、または `SemObserved` のサブタイプ。

# 例

[観測データの置き換え](@ref)に関するオンラインドキュメントを参照してください。
