```
DefaultHanlder
```

DefaultHandlerは、任意の`Formatter`、`IO`、および`Record`を管理します。

フィールド:

  * fmt: `Record`を`String`に変換するための`Formatter`
  * io: `String`を印刷するための`IO`型
  * opts: :is*colorizedや:colorsなどのオプション引数の辞書 例) ```Dict{Symbol, Any}(           :is*colorized => true,           :opts[:colors] => Dict{AbstractString, Symbol}(               "debug" => :blue,               "info" => :green,               ...           )       )```
