```
cm""
```

標準の文字列補間を実装したマークダウンテキスト用の文字列マクロです。補間式の値が埋め込まれたASTを解析して返します。

```julia
value = "interpolated"
cm"Some *$(value)* text."
```

解析に使用されるデフォルトの構文ルールは次のとおりです：

  * `AdmonitionRule`
  * `AttributeRule`
  * `AutoIdentifierRule`
  * `CitationRule`
  * `FootnoteRule`
  * `MathRule`
  * `RawContentRule`
  * `TableRule`
  * `TypographyRule`

これは、`Markdown.@md_str`でサポートされているデフォルトの構文と密接に一致します。

!!! info
    `DollarMathRule`は補間構文と競合するため無効になっています。`MathRule`によって提供される数学のためには、二重バックティックと`math`言語リテラルブロックを使用してください。


`cm""`を使用する際にカスタム`Parser`を呼び出すには、マクロ呼び出しにサフィックスを提供します。例えば：

```julia
more = "more"
cm"Some **$(uppercase(more))** text."none
```

ここで、サフィックス`none`は追加の構文ルールが`enabled!`されていない基本的な`Parser`を呼び出します。例えば、`TypographyRule`のみを有効にするために独自のカスタムパーサーを使用するには、必要なルールが有効な`Parser`オブジェクトを返す現在のモジュールのグローバルスコープからの名前付き関数で呼び出しをサフィックスできます：

```julia
custom() = enable!(Parser(), TypographyRule())
```

次のように使用できます：

```julia
str = "custom"
cm"A '$(titlecase(str))' parser..."custom
```
