パスワード入力 (`<input type="password">`) - ユーザーはテキストを入力でき、テキストは `@bind` を介して `String` として返されます。

これは特別なセキュリティ対策を提供するものではなく、入力された文字の代わりに黒いドット (•••) を表示するだけです。

`default` を使用して初期値を設定します。

[Mozillaの `<input type="password">` に関するドキュメント](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/password) を参照してください。

# 例

`@bind secret_poem PasswordField()`

`@bind secret_poem PasswordField(default="Te dansen omdat men leeft")`
