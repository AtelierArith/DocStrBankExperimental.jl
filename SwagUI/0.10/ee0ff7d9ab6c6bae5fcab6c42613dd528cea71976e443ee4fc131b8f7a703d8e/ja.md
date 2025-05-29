```
render_swagger(swagger_doc::Union{Dict{String, Any}, Nothing};
               options=nothing, kw...)
```

オプションに基づいて、Swagger UIのHTMLを`String`としてレンダリングします。妥当な`swagger_doc`が渡された場合、`Options.swagger_options`の`url`および`urls`はUIによって無視されます。`swagger_doc`が`nothing`の場合、`Options.swagger_options`に`url`または`urls`を含める必要があります。

オプションは`Options`構造体として、またはキーワード引数を介して間接的に渡すことができます（`Options`を参照）。

# 引数

必須:

  * `swagger_doc::Union{Dict{String, Any}, Nothing}` : Swagger仕様ファイル`swagger.json`を`Dict{String, Any}`として。
