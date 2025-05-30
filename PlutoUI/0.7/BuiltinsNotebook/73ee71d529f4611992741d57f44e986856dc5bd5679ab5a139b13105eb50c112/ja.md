テキスト入力 (`<input type="text">`) - ユーザーはテキストを入力でき、テキストは `@bind` を介して `String` として返されます。

`dims` がタプル `(cols::Integer, row::Integer)` の場合、指定された寸法の `<textarea>` が表示されます。

`default` を使用して初期値を設定します。

[Mozilla の `<input type="text">` に関するドキュメント](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/text) と [`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea) を参照してください。

# 例

`@bind poem TextField()`

`@bind poem TextField((30,5); default="Hello JuliaCon!")`
