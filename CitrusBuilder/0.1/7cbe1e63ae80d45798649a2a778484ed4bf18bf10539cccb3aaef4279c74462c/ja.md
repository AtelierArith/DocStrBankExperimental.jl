```
question_group(id, language_settings::LanguageSettings; children)
```

多言語の質問グループを構築します。`children`は省略可能なキーワード引数です。

# 例

```julia-repl
julia> g = question_group(1, language_settings([
    language_setting("de", "Eine Fragengruppe"),
    language_setting("en", "A question group")
]))
```
