```
LogLevel(level)
```

ログレコードの重要度/冗長性。

ログレベルは、ログレコードデータ構造自体を構築する前に、潜在的なログレコードをフィルタリングするためのキーを提供します。

# 例

```julia-repl
julia> Logging.LogLevel(0) == Logging.Info
true
```
