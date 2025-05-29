```
gitrepl()
gitrepl(; kwargs...)
```

Git REPLモードを設定します。

## オプションのキーワード引数

| 名前            | 型                | デフォルト値                       |
|:------------- |:---------------- |:---------------------------- |
| `mode_name`   | `AbstractString` | `"GitREPL.jl Git REPL mode"` |
| `prompt_text` | `AbstractString` | `"git> "`                    |
| `start_key`   | `AbstractChar`   | `','`                        |

## オプションのキーワード引数の説明:

| 名前            | 説明                              |
|:------------- |:------------------------------- |
| `mode_name`   | REPLモードの名前                      |
| `prompt_text` | REPLモードがアクティブなときに表示されるプロンプトテキスト |
| `start_key`   | REPLモードに入るために押すキー               |
