```
support_label(method::GenerativeDerivativeMethod)
```

`method` に関連付けられたサポートラベルを返します。存在しない場合はエラーになります。これは、`method` の型に対して [`generative_support_info`](@ref generative_support_info(::AbstractDerivativeMethod)) が定義されていることに依存します。
