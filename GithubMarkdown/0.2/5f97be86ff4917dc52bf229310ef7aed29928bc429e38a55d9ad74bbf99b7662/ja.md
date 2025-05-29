```
rendergfm(output::IO, input::IO; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
rendergfm(output::IO, input::AbstractString; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
rendergfm(output::AbstractString, input::AbstractString; documenter = false, format="html", removehtml = false, extensions=EXTENSIONS)
```

Markdownドキュメント`input`を`output`にレンダリングし、cmark-gfm仕様に従います。

  * `documenter`: 指定されたフォーマットのDocumenter `@raw`ブロックで出力をラップします。
  * `format`: `html`、`xml`、`man`、`commonmark`、`plaintext`、`latex`のいずれかになります。
  * `removehtml`: `true`の場合、すべてのリテラルHTML入力と潜在的に危険なリンクを削除します。デフォルトは`false`です。`tagfilter`拡張（デフォルトで有効）は、ほとんどの悪意のある生HTMLを削除します。`removehtml == false`の場合は、結果のHTMLをサニタイズすることをお勧めします。
  * `extensions`: 使用する拡張の配列です。有効な拡張は`footnotes`、`table`、`strikethrough`、`autolink`、`tagfilter`、`tasklist`です。これらはすべてデフォルトで有効です。

仕様: https://github.github.com/gfm/
