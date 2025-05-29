```julia
open_file_logger(func::Function, filename::String) -> Any
open_file_logger(
    func::Function,
    filename::String,
    level
) -> Any
open_file_logger(
    func::Function,
    filename::String,
    level,
    mode
) -> Any

```

`Logging.SimpleLogger`を使用してファイルロガーを開きます。

# 引数

  * `func::Function`
  * `filename::String`: ロガーファイル名
  * `level=Logging.Info`: オプション、最小ログレベルを変更するため
  * `mode = "w+"`: オプション、書き込みモードを指定するため

# 例

```Julia
open_file_logger("log.txt", Logging.Info) do logger
    global_logger(logger)
    @info "hello world"
end
```
