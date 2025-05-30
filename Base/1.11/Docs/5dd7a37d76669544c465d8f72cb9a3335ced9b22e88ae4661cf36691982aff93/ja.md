```
apropos([io::IO=stdout], pattern::Union{AbstractString,Regex})
```

`pattern`を含むエントリの利用可能なドキュメント文字列を検索します。

`pattern`が文字列の場合、大文字と小文字は無視されます。結果は`io`に印刷されます。

`apropos`は、クエリを二重引用符で囲むことによってREPLのヘルプモードから呼び出すことができます：

```
help?> "pattern"
```
