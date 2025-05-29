```
validate_code!(errors::Vector{InvalidCodeError}, mi::MethodInstance,
               c::Union{Nothing,CodeInfo})
```

`mi`を検証し、違反があれば`InvalidCodeError`を`errors`に追加してログを記録します。

`isa(c, CodeInfo)`の場合、`validate_code!(errors, c)`も呼び出します。`c`は`mi`に関連付けられた`CodeInfo`インスタンスであると仮定されています。
