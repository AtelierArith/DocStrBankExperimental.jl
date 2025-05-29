```
fmi2GetParameterNames(md::fmi2ModelDescription; vrs=md.parameterValueReferences, mode=:first)
```

パラメータの名前を返します。

# 引数

  * `md::fmi2ModelDescription`: モデル変数の静的情報を提供する構造体。

# キーワード

  * `vrs=md.parameterValueReferences`: モデル記述の追加属性 `parameterValueReferences::Array{fmi2ValueReference}` は、（基本型）変数値へのハンドルです。ハンドルと基本型は変数の値を一意に識別します。（デフォルト = `md.parameterValueReferences::Array{fmi2ValueReference}`）
  * `mode=:first`: 値参照ごとに複数の名前がある場合、利用可能なモードは `:first`（デフォルト、最初のもののみを選択）、`:group`（すべてを選択し、配列にグループ化）、および `:flat`（すべてを選択し、他のすべての名前と一緒に1D配列にフラット化）です。

# 戻り値

  * `names::Array{String}`: パラメータ値参照 `vrs` に対応する名前の配列を返します。
