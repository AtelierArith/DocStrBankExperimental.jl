```
EmptyStackError()
```

データスタック内のコレクションに対して操作を試みましたが、データスタックは空です。

# 例の発生

```julia-repl
julia> getlayer(nothing) # 空のSTACKで
ERROR: EmptyStackError: データコレクションスタックは空です
Stacktrace: [...]
```
