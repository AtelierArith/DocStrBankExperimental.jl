```
numerical_input(id, language_settings::LanguageSettings; minimum=nothing, maximum=nothing, integer_only=false, kwargs...)
numerical_input(id, title::String; help=nothing, kwargs...)
```

多言語対応の数値入力を構築します。

# キーワード引数

  * `minimum`: 最小値
  * `maximum`: 最大値
  * `integer_only`: 整数値のみを許可する
