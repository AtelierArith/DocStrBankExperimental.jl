```
StringDecoder(stream, from, to=enc"UTF-8")
```

新しい読み取り専用I/Oストリームを返し、`stream`から読み取った`from`エンコーディングのテキストを`to`エンコーディングのテキストに変換します。ストリームで`close`を呼び出しても、`stream`は閉じません。

`to`と`from`は、文字列または`Encoding`オブジェクトとして指定できます。
