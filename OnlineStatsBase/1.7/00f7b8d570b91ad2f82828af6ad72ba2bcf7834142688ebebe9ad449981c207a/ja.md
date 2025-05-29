```
TryCatch(stat; error_limit=1000, error_message_limit=90)
```

各`fit!`呼び出しを`try`-`catch`ブロックでラップし、発生したエラーを追跡します（[`CountMap`](@ref)を介して）。`error_limit`のユニークなエラーのみが`CountMap`に含まれます。`error_limit`に達した後に新しいエラーが発生した場合、それは`CountMap`に`"Other"`として含まれます。各エラーメッセージの最初の`error_message_limit`文字のみが記録されます。

# 例

```
o = TryCatch(Mean())

fit!(o, [1, missing, 3])

OnlineStatsBase.errors(o)
```
