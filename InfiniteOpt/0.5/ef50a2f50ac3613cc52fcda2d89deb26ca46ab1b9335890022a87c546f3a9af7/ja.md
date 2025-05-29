```
call_function(fref::ParameterFunctionRef, support...)::Float64
```

`fref`の[`raw_function`](@ref)を、`fref`が定義されたときに与えられた無限パラメータタプルの形式に一致する特定のサポート`support`点で安全に評価します。これは本質的に`raw_function(fref)(supps...)`と同等です。
