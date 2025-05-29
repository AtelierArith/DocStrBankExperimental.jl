```
throw_warning(::FunctionNotMeantToBeUsed)
```

使用されることを意図していない関数が呼び出されたときに警告メッセージを投げます。

# 例

```julia
throw_warning(FunctionNotMeantToBeUsed()) # 特定のメッセージで警告を投げます
```
