```
runexpr(expr::AbstractString)
```

サーバーに文字列として渡されたJuliaコードを実行するように要求します。

# パラメータ

  * expr: サーバーで実行するJuliaコード。

# オプション

  * port: ポート（デフォルト=3000）。
  * output: 実行の出力が表示されるストリーム。
