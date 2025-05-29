```
@report_call [jetconfigs...] f(args...)
```

関数呼び出しへの引数を評価し、その型を決定した後、結果の式に対して[`report_call`](@ref)を呼び出します。このマクロは、`@code_typed`マクロと似たように動作します。

[一般的な設定](@ref)および[エラー分析特有の設定](@ref jetanalysis-config)は、オプションの引数として指定できます。
