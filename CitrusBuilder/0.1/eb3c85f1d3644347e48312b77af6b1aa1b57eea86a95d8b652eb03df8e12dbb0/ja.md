```
short_text_question(id, language_settings::LanguageSettings; kwargs...)
short_text_question(id, title::String; help=nothing, default=nothing, kwargs...)
```

短いテキストの質問を構築します。質問が `title` を使用して構築される場合、グローバルデフォルトの言語がデフォルトで使用されます。

利用可能なキーワード引数のリストについては、[`Question`](@ref)を参照してください。

# 例

単一の言語を使用したシンプルな短いテキストの質問は、`title` 文字列を使用して構築できます。

```julia-repl
julia> q = short_text_question("q1", "my question")
```

多言語の短いテキストの質問を構築するには、[`language_settings`](@ref)を使用します。

```julia-repl
julia> q = short_text_question("q2", language_settings([
    language_setting("en", "question title"),
    language_setting("de", "Fragetitel")
]))
```
