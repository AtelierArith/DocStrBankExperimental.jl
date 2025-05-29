Slackサーバーの設定をレジストリに追加します。`name`パラメータを調整することで、複数のサーバーを定義できます。

# 例

```julia-repl
julia> addConfig(SlackConfig("server.url", "username", "#channel", ":smile:"))
```
