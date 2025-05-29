```
default_language(component::AbstractSurveyComponent)
```

調査コンポーネントのデフォルト言語を返します。デフォルト言語は、コンポーネントの最初の言語として定義されます。

# 例

```julia-repl
julia> g = question_group(1, "group title")
julia> default_language(g)
"en"
```

!!! note
    調査コンポーネントのデフォルト言語は、[`set_default_language!`](@ref)によって設定されたグローバルデフォルト言語と必ずしも等しいわけではありません。


```julia-repl
julia> default_language()
"en"
julia> g = question_group(1, language_settings([
    language_setting("de", "Gruppentitel"),
    language_settings("en", "group title")
]))
julia> default_language(g)
"de"
```
