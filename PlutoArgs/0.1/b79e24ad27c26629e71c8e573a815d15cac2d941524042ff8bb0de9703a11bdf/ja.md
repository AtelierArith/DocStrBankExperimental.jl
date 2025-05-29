```
Arg(name::String, element; required=true, short_name=nothing, type=nothing)
```

Plutoから実行されていない場合、CLIオプションとして –<name> というPluto要素のラッパーを構築します。

キーワード引数:

  * `required`: このオプションをCLIから実行する際に渡す必要があるかどうか。`required == false`の場合、オプションが渡されていないときは、PlutoUI要素の`initial_value`が使用されます。
  * `short_name`: 単一ダッシュの短いCLI名。例えば "k" を渡すと -k になります。
  * `type`: CLI引数を変換するための型をオーバーライドします。`nothing`の場合、`initial_value`の型が考慮されます。
  * `args`: CLI引数（デフォルトは `ARGS`）
