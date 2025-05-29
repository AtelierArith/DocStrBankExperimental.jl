```
array_question(id, language_settings::LanguageSettings, options::VectorOrElemenet{ResponseScale}; subquestions, type="default", kwargs...)
array_question(id, title::String, options::VectorOrElement{ResponseScale}; help=nothing, kwargs...)
array_question(children::Function, id, language_settings::LanguageSettings, options; kwargs...)
array_question(children::Function, id, title::String, options; kwargs...)
```

配列質問を構築します。

質問の `type` を指定して、どの種類の配列質問を構築するかを決定します。`type="dual"` の場合、2つの [`ResponseScale`](@ref) の配列を提供する必要があります。それ以外の場合は、単一の [`ResponseScale`](@ref) が必要です。

# 利用可能なタイプ

  * `"default"`: 配列
  * `"text"`: 配列 (テキスト)
  * `"dropdown"`: 配列 (数値)
  * `"dual"`: 配列デュアルスケール
  * `"bycolumn"`: 列ごとの配列
