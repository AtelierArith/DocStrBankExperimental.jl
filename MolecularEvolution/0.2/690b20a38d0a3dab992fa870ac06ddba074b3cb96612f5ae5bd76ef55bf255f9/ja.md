# 概要

`struct StandardUpdate <: AbstractUpdate`

標準更新は、[`nni_update!`](@ref)、[`branchlength_update!`](@ref)、[`root_update!`](@ref) およびモデル更新への呼び出しのファミリーである可能性があります。

# コンストラクタ

```
StandardUpdate(
    nni::Int,
    branchlength::Int,
    root::Int,
    models::Int,
    refresh::Bool,
    nni_selection::Function,
    branchlength_modifier::UnivariateModifier,
    root_update::RootUpdate,
    models_update::ModelsUpdate
)
```

# 引数

  * `nni::Int`: `nni_update!` によって木を更新する回数
  * `branchlength::Int`: `branchlength_update!` によって木を更新する回数
  * `root::Int`: `root_update!` によって木を更新する回数
  * `models::Int`: モデルを更新する回数
  * `refresh::Bool`: 更新操作の間に木のメッセージを更新してメッセージの一貫性を確保するかどうか
  * `nni_selection::Function`: nni 構成の間で選択する関数
  * `branchlength_modifier::UnivariateModifier`: `branchlength_update!` によって branchlength を更新するための修飾子
  * `root_update::RootUpdate`: `root_update!` によってルートを更新
  * `models_update::ModelsUpdate`: モデルパラメータを更新

関連情報: [`BayesUpdate`](@ref)、[`MaxLikUpdate`](@ref)
