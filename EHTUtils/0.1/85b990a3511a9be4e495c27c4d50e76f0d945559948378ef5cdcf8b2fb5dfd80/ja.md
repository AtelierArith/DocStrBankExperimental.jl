```
@throwerror 例外メッセージ
```

与えられた `message` でエラーをログに記録し、その後同じメッセージで与えられた例外 (`e`) をスローします。

# 例

```julia-repl
julia> @throwerror ArgumentError "エラーメッセージ"
┌ エラー: エラーメッセージ
└ @ Main <PATH>/EHTUtils/src/logging.jl:8
ERROR: ArgumentError: エラーメッセージ
Stacktrace:
 [1] top-level scope
   @ logging.jl:8
```
