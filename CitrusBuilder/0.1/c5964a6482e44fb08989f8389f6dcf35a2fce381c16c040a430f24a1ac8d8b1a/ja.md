```
language_settings(settings; same_default=false)
language_settings(language, title; same_default=false, kwargs...)
```

調査コンポーネントのための `LanguageSettings` を構築します。単一の設定は、`settings::Vector{LanguageSetting}`（[`language_setting`](@ref)も参照）として提供されるか、`language` と `title` の組み合わせとして提供されることができます。

複数の言語が提供され、`same_default=true` の場合、デフォルト言語の `default` 値は他のすべての言語に引き継がれます。

# 例

単一の言語のための言語設定の簡単な構築：

```julia
language_settings("de", "Ein Titel")
```

複数の言語が必要な場合は、[`language_setting`](@ref) のベクトルを使用して設定を構築します。

```julia
language_settings([
    language_setting("en", "A title"),
    language_setting("de", "Ein Titel")
])
```

デフォルト言語の `default` 値を引き継ぐには、`same_default` を使用できます。

```julia
language_settings([
    language_setting("en", "title", default="placeholder value"),
    language_setting("de", "Titel")
], same_default=true)
```
