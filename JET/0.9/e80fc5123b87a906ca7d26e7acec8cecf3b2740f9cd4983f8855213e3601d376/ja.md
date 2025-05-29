```
report_opt(f, [types]; jetconfigs...) -> JETCallResult
report_opt(tt::Type{<:Tuple}; jetconfigs...) -> JETCallResult
report_opt(mi::Core.MethodInstance; jetconfigs...) -> JETCallResult
```

与えられた型シグネチャを持つ関数呼び出しを分析し、最適化の失敗や未解決のメソッドディスパッチを検出します。

[一般的な設定](@ref)および[最適化分析特有の設定](@ref optanalysis-config)は、キーワード引数として指定できます。

詳細については、[最適化分析のドキュメント](@ref optanalysis)を参照してください。
