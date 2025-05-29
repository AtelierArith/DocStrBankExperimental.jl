```
help(component::AbstractSurveyComponent, language::String)
```

指定された言語の調査コンポーネントのヘルプ文字列を返します。`language`が提供されていない場合は、コンポーネントのデフォルト言語のヘルプが返されます。

# 例

```julia-repl
julia> q = short_text_question("q1", "my question", help="some help")
julia> help(q)
"some help"
```
