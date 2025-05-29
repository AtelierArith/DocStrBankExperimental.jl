```
Styled(value; color, bold, italic, underline)
```

`value`をラップする`Styled`オブジェクトを作成し、これらのオプションプロパティに従って`value`をフォーマットします：

  * `bold::Union{Nothing,Bool}`
  * `italic::Union{Nothing,Bool}`
  * `underline::Union{Nothing,Bool}`
  * `color::Union{Nothing,String}` テキストの色を#FA03C7のような16進RGB文字列で指定します。LaTeXでカラーテキストを使用するには、`\usepackage{xcolor}`を追加する必要があります。
