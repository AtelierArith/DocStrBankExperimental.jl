```julia
configure_logging(
;
    console_level,
    file_level,
    filename
) -> InfrastructureSystems.MultiLogger

```

コンソールとファイルのロガーを作成します。

**注意:** ログメッセージは、返されたロガーに対してflush()またはclose()が呼び出されるまで、ファイルに書き込まれない場合があります。

# 引数

  * `console_level = Logging.Error`: コンソールメッセージのレベル
  * `file_level = Logging.Info`: ファイルメッセージのレベル
  * `filename::Union{Nothing, AbstractString} = "power-systems.log"`: ログファイル; ファイルロギングを無効にするにはnothingを渡します

# 例

```julia
logger = configure_logging(console_level = Logging.Info)
@info "log message"
close(logger)
```
