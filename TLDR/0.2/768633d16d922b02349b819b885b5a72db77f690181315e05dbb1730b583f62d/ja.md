```
tldr(str, print=true)
```

`tldr`の主な関数で、`tldr>` REPLまたは`tldr"str"`が使用されるときに呼び出されます。渡された`str`は、どのような検索が行われるかを決定します。

  * `str`は`?`または`help`であり、`tldr> pkg:tldr`と同等です。
  * `str = pkg:something`：パッケージ`something`に関連するコマンドを検索します。
  * `str = cmd:something`：`something`に一致するコマンドを検索します。
  * `str = something`：`cmd:something`と同等です。
