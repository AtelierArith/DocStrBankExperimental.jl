```
report_call(f, [types]; jetconfigs...) -> JETCallResult
report_call(tt::Type{<:Tuple}; jetconfigs...) -> JETCallResult
report_call(mi::Core.MethodInstance; jetconfigs...) -> JETCallResult
```

与えられた型シグネチャを持つ関数呼び出しを分析し、型レベルのエラーを見つけて検出された問題を返します。

[一般的な設定](@ref) および [エラー分析特有の設定](@ref jetanalysis-config) はキーワード引数として指定できます。

詳細については、[エラー分析のドキュメント](@ref jetanalysis) を参照してください。
