```
new_entry(pkg, kind, cmd, description, tags)
```

`TLDR.data`に新しいエントリを作成し、正しい順序で追加します。おそらく`new_pkg`または`new_snippet`の方が良いでしょう。

いくつかのルール：

  * すべてのエントリは文字列であるべきですが、`tags`は文字列の配列であるべきです。
  * `pkg`は大文字小文字を区別するパッケージ名であるべきです（.jlは不要）、例："TLDR"。
  * `kind`は`header`または`snippet`のいずれかであるべきです。
  * `tags`は空であってはいけません。
  * `kind`が`header`の場合、`cmd`は""であるべきです。
