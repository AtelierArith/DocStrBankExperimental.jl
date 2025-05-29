```
setLoggerMode!(mode::Symbol)
```

ALEインスタンスのLoggerのモードを設定します。利用可能なモードは3つ(::Symbol)です。     :info    ==> すべての詳細と情報をログに記録     :warning ==> 警告とエラーをログに記録     :error   ==> エラーのみをログに記録

# 例

```julia-repl
julia> setLoggerMode!(:info)
```
