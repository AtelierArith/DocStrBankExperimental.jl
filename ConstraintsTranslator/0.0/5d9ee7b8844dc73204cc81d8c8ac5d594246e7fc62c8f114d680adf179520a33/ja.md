```
parse_code(s::String)
```

入力文字列 `s` の中で三重バックティックとオプションの言語注釈で区切られたコードブロックを解析します。言語によってキー付けされた辞書を返します。同じ言語のコードブロックは連結されます。
