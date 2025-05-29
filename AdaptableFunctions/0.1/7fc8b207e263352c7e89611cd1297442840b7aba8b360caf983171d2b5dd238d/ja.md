```
struct UnadaptedFunction{F,T} <: Function
```

インスタンス `FunctionNotAdaptable{F,T}()` は、タイプ `F` の関数がタイプ `T` の入力に適応できないことを示します。

`(f::UnadaptedFunction).f``は元の関数を含み、`(f::UnadaptedFunction)(args...; kwargs...)` は元の関数を呼び出します。
