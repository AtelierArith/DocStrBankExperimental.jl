```
(1) SemEnsemble(models...; weights = nothing, kwargs...)

(2) SemEnsemble(;specification, data, groups, column = :group, kwargs...)
```

アンサンブルモデルのコンストラクタです。(2) はマルチグループモデルを便利に指定するために使用できます。

# 引数

  * `models...`: `AbstractSem`s。
  * `weights::Vector`: 各モデルの重み。観測データポイントの数がデフォルトです。
  * `specification::EnsembleParameterTable`: モデル仕様。
  * `data::DataFrame`: 観測データ。`column` に `Vector{Symbol}` 型のグループを含む必要があります。
  * `groups::Vector{Symbol}`: グループ名。
  * `column::Symbol`: `data` 内のグループを含む列の名前。

すべての追加の kwargs はモデル部分に渡されます。

次のフィールドを持つ SemEnsemble を返します。

  * `n::Int`: モデルの数。
  * `sems::Tuple`: `AbstractSem`s。
  * `weights::Vector`: 各モデルの重み。
  * `param_labels::Vector`: パラメータラベルとその位置を格納します。

マルチグループモデルに関する指示については、オンラインドキュメントを参照してください。
