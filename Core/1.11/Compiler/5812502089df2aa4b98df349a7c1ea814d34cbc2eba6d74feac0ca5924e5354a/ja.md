```
add_remark!(::AbstractInterpreter, sv::InferenceState, remark)
```

現在の行（すなわち `sv.currpc`）の推論中に分析の備考を出力します。これらの注釈はデフォルトでは無視されますが、外部ツールによって推論結果に注釈を付けるために使用できます。
