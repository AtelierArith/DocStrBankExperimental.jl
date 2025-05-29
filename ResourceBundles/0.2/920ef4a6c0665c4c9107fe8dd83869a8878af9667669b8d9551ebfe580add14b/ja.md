```
string_to_key(text::AbstractString)
```

テキストをキーに変換します。補間構文を標準化された補間整数に置き換えます。明示的な素性なしの例: `string_to_key("text$var $(expr) $(77)") == "text1 2 3"` 明示的な素性のある例: `string_to_key("text$var $(!(expr)) $(77)") == "text2 1 3"` （最初の補間に '`!`' が付けられたものは番号1を取得します）。補間はリテラル文字列であってはなりません。
