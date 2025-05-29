```
tokenize(text; operators_as_identifiers=true)
```

UTF-8エンコードされた`text`を`Token`のベクターとしてトークン化して返します。トークンのテキストは`untokenize()`を使用して取得できます。完全なテキストは、例えば`join(untokenize.(tokenize(text), text))`を使って再構築できます。

このインターフェースは、UTF-8エンコードされた文字列またはバッファデータのみに対応しています。

キーワード`operators_as_identifiers`は、識別子位置における演算子が`K"Identifier"`として扱われるべきか、より具体的な演算子の種類として出力されるべきかを指定します。例えば、`a + b`の`+`が`K"Identifier"`（デフォルト）として出力されるべきか、`K"+"`として出力されるべきかを決定します。
